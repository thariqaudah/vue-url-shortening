<template>
	<header class="app-header">
		<div class="container">
			<div class="logo">
				<img src="../assets/logo.svg" alt="" />
			</div>

			<nav class="navigation">
				<ul class="navigation-list">
					<li><a href="#" class="link">Features</a></li>
					<li><a href="#" class="link">Pricing</a></li>
					<li><a href="#" class="link">Resources</a></li>
				</ul>

				<ul class="auth-list">
					<li><a href="#" class="link">Login</a></li>
					<li><a href="#" class="link hl">Sign Up</a></li>
				</ul>
			</nav>

			<button class="btn-toggle">
				<i class="fas fa-bars"></i>
			</button>
		</div>
	</header>
</template>

<script>
export default {
	name: 'AppHeader',
};
</script>

<style lang="scss" scoped>
.app-header {
	padding: 24px 0;
	.container {
		display: flex;
		align-items: center;
	}

	.logo {
		display: flex;
		align-items: center;
		margin-right: 48px;
	}

	.navigation {
		display: flex;
		width: 100%;

		@media (max-width: 375px) {
			display: none;
		}

		ul {
			list-style: none;
			display: flex;
			align-items: center;
			gap: 24px;

			&.auth-list {
				margin-left: auto;
				gap: 32px;
			}

			.link {
				font-weight: 500;
				text-decoration: none;
				color: #9e9aa7;
				transition: all 0.3s ease-out;

				&.hl {
					background-color: #2acfcf;
					color: #fff;
					padding: 8px 24px;
					border-radius: 100px;

					&:hover,
					&:active {
						background-color: rgba(42, 207, 207, 0.6);
						color: #fff;
					}
				}

				&:hover,
				&:active {
					color: #232127;
				}
			}
		}
	}

	.btn-toggle {
		display: none;

		@media (max-width: 375px) {
			display: block;
			background: none;
			border: none;
			margin-left: auto;
			cursor: pointer;

			i {
				font-size: 24px;
				color: hsl(257, 7%, 63%);
			}
		}
	}
}
</style>
