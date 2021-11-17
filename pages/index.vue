<template>
  <div class="page">
    <Menu :pages="pages" />
    <NuxtContent :document="content" class="markdown prose" />
    <div class="dynamic-content">
      <h3>Posts</h3>
      <ul>
        <li v-for="(post, p) in posts.filter(po => !!po.path)" :key="`post-${p}`">
          <NuxtLink :to="`/posts/${post.slug}`">
            {{ post.title }} <sub>{{ formatDate(post.createdAt) }}</sub>
          </NuxtLink>
        </li>
      </ul>
      <template v-for="(type, t) in ['past', 'upcoming']">
        <template v-if="events[type].length > 0">
          <h3 v-text="`${type} events`" />
          <ul>
            <li v-for="(event, e) in events[type].filter(ev => !!ev.path)" :key="`${type}-event-${e}`">
              <NuxtLink :to="event.path">
                <h5 v-text="event.title" />
              </NuxtLink>
            </li>
          </ul>
        </template>
      </template>
    </div>
  </div>
</template>

<script>
import Menu from '~/components/Menu.vue'
export default {
  async asyncData({ $content, params }) {
    /**
     * Get the page content
     */
    const content = await $content('pages', 'index').fetch()
    /**
     * Get events and split them into two
     */
    const events = await $content('events').only(['title', 'date']).sortBy('date', 'asc').fetch()
    const pastEvents = events.filter(e => new Date(e.date).getDate() > new Date().getDate())
    const upcomingEvents = events.filter(e => new Date(e.date).getDate() < new Date().getDate())
    /**
     * Get the posts ordered by created at
     */
    const posts = await $content('posts').sortBy('createdAt', 'desc').fetch()
    /**
     * Get the other pages to push them into the menu
     */
    const pages = await $content('pages').sortBy('order', 'asc').fetch()
    /**
     * Return the fetched elements
     */
    return { content, events: { past: pastEvents, upcoming: upcomingEvents }, posts, pages }
  },
  layout: 'default',
  components: { Menu },
  methods: {
    formatDate: (date) => {
      const options = { year: '2-digit', month: 'short', day: 'numeric' }
      return new Date(date).toLocaleString('en-GB', options)
    }
  }
}
</script>


<style lang="scss">
p {
  white-space: break-spaces;
}
a {
  text-decoration: none;
  font-weight: bold;
  sub {
    font-size: .65em;
  }
}
.dynamic-content {
  h3 {
    text-transform: uppercase;
    font-size: .9em;
    border-bottom: 1px dotted darkgray;
  }
  ul {
    padding-left: 1em;
  }
}
</style>
