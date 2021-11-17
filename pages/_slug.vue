<template>
<div class="page">
	<Menu :pages="pages" />
	<NuxtContent :document="page" />
</div>
</template>

<script>
export default {
	async asyncData({ $content, params }) {
		const page = await $content('pages', params.slug).fetch()
		const pages = await $content('pages').sortBy('order', 'asc').fetch()
		return { page, pages }
	},
	name: "Page",
	layout: 'default'
}
</script>