<template>
<div class="scol-page">
	<NuxtContent :document="doc" />
</div>
</template>

<script>
export default {
	async asyncData({ $content, params }) {
		const doc = await $content(`scol/${params.year}`, 'index').fetch()
		const scol = await $content(`scol/${params.year}`).only(['title', 'date']).sortBy('date', 'asc').fetch()
		return { doc, scol }
	},
	name: "ScolPage"
}
</script>
