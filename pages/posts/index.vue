<template>
<div class="post-page">
	<NuxtContent :document="doc" />
</div>
</template>

<script>
export default {
	async asyncData({ $content, params }) {
		const doc = await $content('posts', 'index').fetch()
		const posts = await $content('posts').only(['title', 'isIndex', 'createdAt']).sortBy('date', 'desc').fetch()
		return { doc, posts }
	},
	name: "PostsPage",
	methods: {
		formatDate (date) {
			const options = { year: '2-digit', month: 'short', day: 'numeric' }
			return new Date(date).toLocaleString('en-GB', options)
		}
	}
}
</script>
