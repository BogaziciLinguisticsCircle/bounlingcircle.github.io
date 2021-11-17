<template>
	<div class="post-page">
		<NuxtContent :document="post" />
	</div>	
</template>

<script>
export default {
	async asyncData({ $content, params }) {
		const post = await $content('posts', params.slug).fetch()
		return { post }
	},
	name: 'PostPage'
}
</script>
