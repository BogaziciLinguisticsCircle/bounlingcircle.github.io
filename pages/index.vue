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
