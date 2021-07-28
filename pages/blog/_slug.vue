<template>
	<div>
		<h1 class="text-indigo-600">{{ document.title }}</h1>
		<div class="prose w-full max-w-full">
			<nuxt-content :document="document" />
		</div>
	</div>
</template>

<script>
export default {
 async asyncData({ $content, params  }) {
    const document = await $content("blog", params.slug).fetch();
    return { document };
 },
 head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
}
</script>
