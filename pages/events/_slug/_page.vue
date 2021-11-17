<template>
	<div class="event-page">
		<NuxtContent :document="eventPage" />
	</div>
</template>

<script>
export default {
	async asyncData({ $content, params }) {
		const eventPage = await $content(`events/${params.slug}`, params.page).fetch()
		return { eventPage }
	},
	name: "EventPage"
}
</script>
