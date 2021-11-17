<template>
  <div class="main-page">
    <NuxtContent :document="content" class="markdown prose" />
    <div class="dynamic-content">
      <h3>Posts</h3>
      <ul>
        <li v-for="(post, p) in posts" :key="`post-${p}`">
          <nuxt-link :to="`/posts/${post.slug}`">
            {{ post.title }} <sub>{{ formatDate(post.createdAt) }}</sub>
          </nuxt-link>
        </li>
      </ul>
      <template v-for="(type, t) in ['past', 'upcoming']">
        <h3 v-text="`${type} events`" />
        <li v-for="(event, e) in events[type]" :key="`${type}-event-${e}`">
          <nuxt-link :to="event.path">
            <h5 v-text="event.title" />
          </nuxt-link>
        </li>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const content = await $content('pages', 'index').fetch()
    const events = await $content('events')
      .only(['title', 'date'])
      .sortBy('date', 'asc')
      .fetch()
    const pastEvents = events.filter(e => new Date(e.date).getDate() > new Date().getDate())
    const upcomingEvents = events.filter(e => new Date(e.date).getDate() < new Date().getDate())
    const posts = await $content('posts')
      .sortBy('createdAt', 'desc')
      .fetch()
    return { content, events: { past: pastEvents, upcoming: upcomingEvents }, posts }
  },
  layout: 'default',
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
}
</style>
