<template>
	<section class="error-container">
		<p class="not-found" v-if="error.statusCode === 404">
			Ceci n'est pas une page.
		</p>
		<p v-else class="not-found">
			An error occured
		</p>
    <NuxtLink to="/">← Go Back</NuxtLink>
	</section>
</template>

<script>
export default {
	props: ['error'],
	layout: 'error'
}
</script>

<style lang="scss">
	.error-container {
		display: flex;
		justify-content: center;
		flex-wrap: wrap;
		flex-direction: column;
	}
	.not-found {
		border: 2px solid black;
		border-left: none;
		border-right: none;
		font-size: 2em;
		font-family: 'Passions Conflict', cursive;
		font-weight: bolder;
		text-align: center;
		&:before {
			content: "📃\A";
			white-space: pre;
		}
	}
</style>