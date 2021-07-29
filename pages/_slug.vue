<template>
	<div>
		<div v-for="t in document.team">
			<Hero v-if="t.type == 'hero,'" :title="t.title"/>
			<h1 v-if="t.type == 'prices,'">Prices</h1>
			<h1 v-if="t.type == 'fake,'">Prices</h1>
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
	showTeam: function(){
		console.log(this.document.team, "team");
	},
 },
 head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
}
</script>
