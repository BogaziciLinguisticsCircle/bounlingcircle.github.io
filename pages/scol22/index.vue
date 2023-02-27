<template>
<div class="scol-page">
	<NuxtContent :document="doc" />
</div>
</template>

<script>
export default {
	async asyncData({ $content, params }) {
		const doc = await $content('scol/22', 'index').fetch()
		const scol22 = await $content('scol/22').only(['title', 'date']).sortBy('date', 'asc').fetch()
		return { doc, scol22 }
	},
	name: "ScolPage"
}
</script>
