<template>
<div class="post-page">
	<NuxtContent :document="doc" />
	<h3>List of all posts</h3>
	<ul>
		<template v-for="(post, e) in posts.filter(post => post.isIndex !== true && post.path)">
			<li :key="`post-${i}`">
				<NuxtLink :to="post.path" v-text="post.title" />
				<sub v-text="formatDate(post.createdAt)" />
			</li>
		</template>
	</ul>
</div>
</template>

<script>
export default {
	async asyncData({ $content, params }) {
		const doc = await $content('posts', 'index').fetch()
		const posts = await $content('posts').only(['title', 'isIndex', 'createdAt']).sortBy('date', 'desc').fetch()
		return { doc, posts }
	},
	name: "PostsPage",
	methods: {
		formatDate (date) {
			const options = { year: '2-digit', month: 'short', day: 'numeric' }
			return new Date(date).toLocaleString('en-GB', options)
		}
	}
}
</script>

<style lang="scss">
.post-page {
	sub {
		font-size: .6em;
	}
}
</style>