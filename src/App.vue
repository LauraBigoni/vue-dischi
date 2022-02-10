<template>
	<div id="app">
		<Header />
		<main>
			<Dischi />
		</main>
		<Footer />
	</div>
</template>

<script>
import Header from "./components/Header.vue";
import Dischi from "./components/Dischi.vue";
import Footer from "./components/Footer.vue";

export default {
	name: "App",
	components: {
		Header,
		Dischi,
		Footer,
	},
};
</script>

<style lang="scss">
@import "./assets/scss/style.scss";
</style>
