<template>
	<div class="scol-page">
		<NuxtContent :document="scolPage" />
	</div>
</template>

<script>
export default {
	async asyncData({ $content, params }) {
		const scolPage = await $content(`scol21/${params.slug}`, params.page).fetch()
		return { scolPage }
	},
	name: "ScolPage"
}
</script>
