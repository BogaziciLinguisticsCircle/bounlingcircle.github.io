<template>
  <div class="page">
    <NuxtContent :document="doc" class="markdown prose" />
  </div>
  <Modal v-show="showModal" @close-modal="showModal = false" />
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
import Modal from '/components/Modal.vue'

export default {
  components: { Modal },
  data() {
    return {
      showModal: true,
    }
  },
}
</script>
