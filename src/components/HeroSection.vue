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
	padding: 96px 0;

	.container {
		display: flex;
		align-items: center;
		gap: 48px;

		.hero-text {
			padding-right: 120px;

			.lead {
				font-size: 20px;
				line-height: 1.6;
				margin-bottom: 32px;
			}
		}
	}
}
</style>
