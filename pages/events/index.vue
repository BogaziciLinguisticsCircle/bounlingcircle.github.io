<template>
<div class="event-page">
	<NuxtContent :document="doc" />
</div>
</template>

<script>
export default {
	async asyncData({ $content, params }) {
		const doc = await $content('events', 'index').fetch()
		const events = await $content('events').only(['title', 'date']).sortBy('date', 'asc').fetch()
		return { doc, events }
	},
	name: "EventsPage"
}
</script>

<style lang="scss">
</style>