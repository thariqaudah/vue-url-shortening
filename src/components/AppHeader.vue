<template>
	<header class="app-header">
		<div class="container">
			<div class="logo">
				<img src="../assets/logo.svg" alt="" />
			</div>

			<nav class="navigation" v-if="!mobile">
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

			<button
				class="btn-toggle"
				:class="{ 'mobile-open': mobileNav }"
				v-if="mobile"
				@click="mobileNav = !mobileNav"
			>
				<i class="fas fa-bars"></i>
			</button>

			<transition name="drop-menu">
				<nav class="navigation mobile-navigation" v-if="mobileNav">
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
			</transition>
		</div>
	</header>
</template>

<script>
import { onMounted, ref } from 'vue';

export default {
	name: 'AppHeader',
	setup() {
		const windowWidth = ref(null);
		const mobile = ref(null);
		const mobileNav = ref(null);

		const watchScreen = () => {
			windowWidth.value = window.innerWidth;
			if (windowWidth.value <= 375) {
				mobile.value = true;
				return;
			}
			mobile.value = false;
			mobileNav.value = false;
		};

		onMounted(() => {
			window.addEventListener('resize', watchScreen);
			watchScreen();
		});

		return { windowWidth, mobile, mobileNav };
	},
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
				font-size: 16px;
				font-weight: 700;
				text-decoration: none;
				color: #9e9aa7;
				transition: all 0.3s ease-out;

				&.hl {
					display: inline-block;
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

		&.mobile-navigation {
			flex-direction: column;
			background-color: #3b3054;
			width: calc(100% - 48px);
			position: absolute;
			top: 81px;
			left: 50%;
			transform: translateX(-50%);
			padding: 32px 24px;
			border-radius: 9px;

			ul {
				flex-direction: column;
				gap: 32px;

				&.auth-list {
					width: 100%;
					margin-top: 32px;
					padding-top: 32px;
					border-top: 1px solid #666;

					li:last-child {
						width: 100%;
						text-align: center;
					}
				}

				.link {
					color: #fff;

					&.hl {
						width: 100%;
						padding: 12px 24px;
					}
				}
			}
		}
	}

	.btn-toggle {
		display: block;
		background: none;
		border: none;
		margin-left: auto;
		cursor: pointer;
		transition: all 0.3s ease-in;

		i {
			font-size: 24px;
			color: hsl(257, 7%, 63%);
		}

		// Rotating animation
		&.mobile-open {
			transform: rotate(180deg);
		}
	}

	.drop-menu-enter-active,
	.drop-menu-leave-active {
		transition: all 0.3s ease-in;
	}

	.drop-menu-enter-from,
	.drop-menu-leave-to {
		opacity: 0;
	}

	.drop-menu-enter-to {
		opacity: 1;
	}
}
</style>
