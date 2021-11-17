<template>
<div class="menu">
	<template v-for="(page, p) in pages">
		<NuxtLink :to="`/${page.slug}`" :key="`menu-item-${p}`" v-text="page.title" />
	</template>
</div>
</template>

<script>
export default {
	name: "Menu",
	props: ['pages'],
	mounted () {
		console.log(this.$router)
	}
}
</script>

<style lang="scss">
.menu {
	display: flex;
	position: absolute;
	top: 1em;
	& > * {
		margin-right: .1em;
		padding: 0 .5em;
		background-color: #fafafa;
		color: black;
		transition: all ease-in-out .3s;
	}
	.nuxt-link-exact-active {
		background-color: #1d1d1d;
		color: white;
	}
}
</style>