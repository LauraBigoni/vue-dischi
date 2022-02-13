<template>
	<div id="app">
		<Header />
		<main>
			<Dischi @change-genre="newTermChange" />
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
	data() {
		return {
			newTerm: '',
		};
	},
	methods: {
		newTermChange(prop) {
			this.newTerm = prop;
		}
	}
};
</script>

<style lang="scss">
@import "./assets/scss/style.scss";
</style>
