<template>
	<div class="app">
		<AppHeader />
		<HeroSection />
		<ShortenForm />
		<StatisticsSection />
	</div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import HeroSection from './components/HeroSection.vue';
import ShortenForm from './components/ShortenForm.vue';
import StatisticsSection from './components/StatisticsSection.vue';

export default {
	name: 'App',
	components: { AppHeader, HeroSection, ShortenForm, StatisticsSection },
};
</script>

<style lang="scss">
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}

body {
	font-size: 18px;
	font-family: 'Poppins', sans-serif;
	color: #9e9aa7;
}

.container {
	width: 100%;
	max-width: 1440px;
	margin: 0 auto;
	padding: 0 24px;
}

.h1 {
	font-size: 62px;
	font-weight: 700;
	line-height: 1.2;
	color: #35323e;
}

.h2 {
	font-size: 42px;
	font-weight: 700;
	line-height: 1.2;
	color: #35323e;
	margin-bottom: 24px;
}

.btn {
	display: inline-block;
	text-decoration: none;
	border: none;
	background-color: #2acfcf;
	color: #fff;
	padding: 16px 40px;
	font-size: 18px;
	font-family: inherit;
	font-weight: 700;
	border-radius: 7px;
	cursor: pointer;
	transition: all 0.3s ease-out;

	&:hover,
	&:active {
		background-color: rgba(42, 207, 207, 0.6);
	}

	&.btn-rounded {
		border-radius: 100px;
	}
}
</style>
