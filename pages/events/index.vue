<template>
<div class="event-page">
	<NuxtContent :document="doc" />
	<h3>List of all events</h3>
	<ul>
		<template v-for="(event, e) in events.filter(e => !!e.date && e.path)">
			<li :key="`event-${i}`">
				<NuxtLink :to="event.path" v-text="event.title" />
			</li>
		</template>
	</ul>
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