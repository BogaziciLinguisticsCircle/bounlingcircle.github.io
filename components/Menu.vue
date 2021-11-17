<template>
<div class="menu">
	<NuxtLink to="/">Home</NuxtLink>
	<NuxtLink to="/events">Events</NuxtLink>
	<NuxtLink to="/posts">Posts</NuxtLink>
</div>
</template>

<script>
export default {
	name: "Menu"
}
</script>

<style lang="scss">
.menu {
	display: flex;
	justify-content: center;
	width: 100%;
	margin-left: -.5em;
	& > * {
		margin-right: .1em;
		padding: 0 .5em;
		background-color: #fafafa;
		color: black;
		transition: all ease-in-out .3s;
		text-decoration: none;
		font-weight: bold;
	}
	.nuxt-link-exact-active {
		background-color: #1d1d1d;
		color: white;
	}
}
</style>