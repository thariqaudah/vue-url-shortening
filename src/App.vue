<template>
  <div class="app">
    <AppHeader />
    <HeroSection />
    <div class="main">
      <ShortenForm />
      <SingleLink />
      <StatisticsSection />
    </div>
    <BoostSection />
    <AppFooter />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import HeroSection from './components/HeroSection.vue';
import ShortenForm from './components/ShortenForm.vue';
import SingleLink from './components/SingleLink.vue';
import StatisticsSection from './components/StatisticsSection.vue';
import BoostSection from './components/BoostSection.vue';
import AppFooter from './components/AppFooter.vue';

export default {
  name: 'App',
  components: {
    AppHeader,
    HeroSection,
    ShortenForm,
    SingleLink,
    StatisticsSection,
    BoostSection,
    AppFooter,
  },
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
  max-width: 1300px;
  margin: 0 auto;
  padding: 0 32px;
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
    background-color: lighten($color: #2acfcf, $amount: 20);
  }

  &.btn-rounded {
    border-radius: 100px;
  }
}
</style>
