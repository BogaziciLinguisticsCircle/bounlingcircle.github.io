<template>
<div class="scol-page">
	<NuxtContent :document="doc" />
</div>
</template>

<script>
export default {
	async asyncData({ $content, params }) {
		const doc = await $content('scol21', 'index').fetch()
		const scol21 = await $content('scol21').only(['title', 'date']).sortBy('date', 'asc').fetch()
		return { doc, scol21 }
	},
	name: "ScolPage"
}
</script>
