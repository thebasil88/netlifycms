<template>
	<div>
		<div v-for="t in document.module">
			<Hero v-if="t.type == 'hero'" 
				  :title="t.title"
				  :title_colored="t.title_colored"
				  :btn2_link="t.btn2_link"
				  :btn1_link="t.btn1_link"
				  :btn2_text="t.btn2_text"
				  :btn1_text="t.btn1_text"
				  :content="t.content"
				  :image="t.image"
			/>
			<Prices v-if="t.type == 'prices'" />
			<h1 v-if="t.type == 'fake'">Prices</h1>
		</div>
	</div>
</template>

<script>
export default {
 async asyncData({ $content }) {
    const document = await $content("pages", 'home').fetch();
	console.log(document);
    return { document };
 },
 head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
}
</script>
