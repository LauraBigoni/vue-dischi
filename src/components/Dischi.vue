<template>
	<div class="container dischi">
		<div class="row text-center">
			<div class="col">
				<ul class="list-unstyled">
					<li v-for="cd in music" :key="cd.author">
						<img class="img-fluid" :src="cd.poster" :alt="cd.title" />
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
			music: [],
			api: "https://flynn.boolean.careers/exercises/api/array/music",
		};
	},
	methods: {
		getMusic(url) {
			axios.get(url).then((res) => {
				this.music = res.data.response;
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
	font-weight: 700;
	img {
		width: 150px;
		height: auto;
	}
}
</style>