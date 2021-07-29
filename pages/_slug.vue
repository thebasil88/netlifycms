<template>
	<div>
		<button @click="showmodule">show module data</button>
		<div v-for="t in document.modules">
			<Hero v-if="t.type == 'hero'" :title="t.title"/>
			<Prices v-if="t.type == 'prices'" />
			<h1 v-if="t.type == 'fake'">Prices</h1>
		</div>
	</div>
</template>

<script>
export default {
 async asyncData({ $content, params  }) {
    const document = await $content("pages", params.slug).fetch();
	
    return { document };
 },
 methods: {
	showmodule: function(){
		console.log(this.document, "module");
	},
 },
 head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
}
</script>
