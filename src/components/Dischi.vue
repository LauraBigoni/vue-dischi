<template>
	<div class="container dischi">
		<div class="row text-center">
			<div class="col">
				<div
					id="loader"
					class="
						text-center
						flex-column
						d-flex
						justify-content-center
						align-items-center
					"
					v-if="isLoading"
				>
					<i class="fa-solid fa-spinner"></i> <br />
					<span>LOADING...</span>
				</div>
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
					<li v-for="cd in music" :key="cd.author">
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

export default {
	name: "Dischi",
	data() {
		return {
			isLoading: false,
			music: [],
			api: "https://flynn.boolean.careers/exercises/api/array/music",
		};
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
	},
	mounted() {
		this.getMusic(this.api);
	},
};
</script>

<style scoped lang="scss">
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
#loader {
	padding: 300px 0;
	letter-spacing: 10px;
	.fa-spinner {
		font-size: 40px;
		animation: rotate 2s infinite linear;
	}
	@keyframes rotate {
		from {
			transform: rotate(0deg);
		}
		to {
			transform: rotate(360deg);
		}
	}
}
</style>