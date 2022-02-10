<template>
	<div class="row m-0">
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
			>
				<i class="fa-solid fa-spinner"></i> <br />
				<span>LOADING...</span>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "Loader",
};
</script>

<style scoped lang="scss">
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