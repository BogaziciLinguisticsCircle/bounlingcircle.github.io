<template>
  <div class="page">
    <NuxtContent :document="doc" class="markdown prose" />
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    /**
     * Get the page content
     */
    const doc = await $content('', 'index').fetch()
    return { doc }
  },
  layout: 'default'
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
