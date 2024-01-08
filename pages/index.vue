<template>
  <div class="page">
    <NuxtContent :document="doc" class="markdown prose" />
    <FModal v-show="showModal" @close-modal="showModal = false" />
  </div>
</template>

<script>
import FModal from '~/components/FlyerModal.vue'

export default {
  components: { FModal },
  data() {
    return {
      showModal: true,
    }
  },
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
