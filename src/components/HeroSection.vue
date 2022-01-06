<template>
	<section class="hero-section">
		<div class="container">
			<div class="hero-text">
				<h1 class="h1">More than just shorter links</h1>
				<p class="lead">
					Build your brand’s recognition and get detailed insights on how your
					links are performing.
				</p>
				<a href="" class="btn btn-rounded">Get Started</a>
			</div>

			<div class="hero-img">
				<img src="../assets/illustration-working.svg" alt="" />
			</div>
		</div>
	</section>
</template>

<script>
export default {
	name: 'HeroSection',
};
</script>

<style lang="scss" scoped>
.hero-section {
	padding: 64px 0 150px 0;

	.container {
		display: flex;
		align-items: center;
		gap: 32px;

		@media (max-width: 375px) {
			flex-direction: column;
		}

		.hero-text {
			// padding-right: 120px;
			@media (max-width: 375px) {
				order: 2;
				text-align: center;
			}

			.lead {
				font-size: 20px;
				line-height: 1.6;
				margin-bottom: 32px;

				@media (max-width: 375px) {
					font-size: 18px;
				}
			}
		}

		.hero-img {
			@media (max-width: 375px) {
				order: 1;
			}
		}
	}
}
</style>
