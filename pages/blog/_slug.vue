<template>
	<div>
		<h1 class="text-indigo-600">HI!</h1>
		<div v-for="document in documents" key="document.slug" class="prose w-full max-w-full">
			<nuxt-content :document="document" />
		</div>
	</div>
</template>

<script>
export default {
 async asyncData({ $content }) {
    const documents = await $content("blog").fetch();
	console.log(documents);
    return { documents };
 },
 head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
}
</script>
