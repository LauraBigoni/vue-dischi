<template>
	<footer>
		<div class="row m-0">
			<div class="col">
				<nav class="d-flex justify-content-center align-items-center p-4">
					<ul class="pagination">
						<li class="page-item disabled">
							<a class="page-link" href="#">Previous</a>
						</li>
						<li class="page-item">
							<a class="page-link" href="#">Next</a>
						</li>
					</ul>
				</nav>
			</div>
		</div>
	</footer>
</template>

<script>
export default {
    name: 'Footer',
};
</script>

<style scoped lang="scss">
@import "../assets/scss/_vars.scss";

.page-link {
	color: $page-link;
}
.page-link:hover, .page-link:focus {
	color: $page-link;
    box-shadow: 0 0 0 0.15rem $page-link;
}
</style>