<template>
	<div class="container dischi">
		<div class="row text-center">
			<div class="col">
				<select
					v-model="genres"
					class="form-select"
					@change="$emit('change-genre', genres)"
				>
					<option value="all">Search genre</option>
					<option
						v-for="(product, index) in filterGenres()"
						:key="index"
						:value="product"
					>
						{{ product }}
					</option>
				</select>
				<Loader v-if="isLoading" />
				<ul
					v-else
					class="
						list-unstyled
						d-flex
						flex-wrap
						justify-content-around
						align-items-start
					"
				>
					<li v-for="cd in removeDuplicates" :key="cd.author">
						<img class="img-fluid" :src="cd.poster" :alt="cd.title" />
						<p class="h5 pt-2">{{ cd.title }}</p>
						<p class="m-0">{{ cd.author }}</p>
						<span>{{ cd.year }}</span>
					</li>
				</ul>
			</div>
		</div>
	</div>
</template>

<script>
import axios from "axios";

import Loader from "./Loader.vue";
export default {
	name: "Dischi",
	components: {
		Loader,
	},
	data() {
		return {
			isLoading: false,
			music: [],
			genres: "all",
			api: "https://flynn.boolean.careers/exercises/api/array/music",
		};
	},
	computed: {
		removeDuplicates() {
			return this.music.filter((el) => {
				if (this.genres == el.genre || el.genre == "" || this.genres == "all")
					return true;
			});
		},
	},
	methods: {
		getMusic(url) {
			this.isLoading = true;
			axios.get(url).then((res) => {
				this.music = res.data.response;
				this.isLoading = false;
				console.log(this.music);
			});
		},
		filterGenres() {
			const filteredMusic = [];
			this.music.forEach((el) => {
				if (!filteredMusic.includes(el.genre)) {
					filteredMusic.push(el.genre);
				}
			});
			return filteredMusic;
		},
	},
	mounted() {
		this.getMusic(this.api);
	},
};
</script>

<style scoped lang="scss">
.form-select {
	width: 100px;
	position: absolute;
	top: 20px;
	right: 50px;
}
.dischi {
	ul {
		padding-top: 30px;
	}
	li {
		width: 220px;
		height: 300px;
		padding: 20px 0;
		margin-bottom: 15px;
		background-color: rgba(255, 255, 255, 0.2);
	}
	img {
		width: 150px;
		height: auto;
	}
	p {
		text-transform: uppercase;
		font-weight: 700;
	}
}
</style>