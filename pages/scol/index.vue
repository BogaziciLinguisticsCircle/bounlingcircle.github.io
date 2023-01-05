<template>
	<section class="not-found-container">
		<p class="not-found">
			This is not a page.
		</p>
	</section>
</template>

<style lang="scss">
	.not-found-container {
		display: flex;
		justify-content: center;
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