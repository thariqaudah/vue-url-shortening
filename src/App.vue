<template>
  <div class="app">
    <AppHeader />
    <HeroSection />
    <div class="main-area">
      <div class="container">
        <ShortenForm @createLink="createLink" />

        <!-- Output short links -->
        <ul class="link-list" v-if="links && links.length > 0">
          <li class="link-item" v-for="(link, index) in links" :key="index">
            <SingleLink
              :link="link"
              @copy="handleCopy"
              :copiedLink="copiedLink"
            />
          </li>
        </ul>
      </div>

      <StatisticsSection />
    </div>
    <BoostSection />
    <AppFooter />
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';
import AppHeader from './components/AppHeader.vue';
import HeroSection from './components/HeroSection.vue';
import ShortenForm from './components/ShortenForm.vue';
import StatisticsSection from './components/StatisticsSection.vue';
import BoostSection from './components/BoostSection.vue';
import AppFooter from './components/AppFooter.vue';
import SingleLink from './components/SingleLink.vue';

export default {
  name: 'App',
  components: {
    AppHeader,
    HeroSection,
    ShortenForm,
    StatisticsSection,
    BoostSection,
    AppFooter,
    SingleLink,
  },
  setup() {
    const links = ref([]);
    const copiedLink = ref(null);

    const createLink = newLink => {
      links.value.unshift(newLink);
      window.localStorage.setItem('links', JSON.stringify(links.value));
    };

    const handleCopy = async () => {
      const clipText = await navigator.clipboard.readText();
      copiedLink.value = clipText;
    };

    onMounted(() => {
      const data = JSON.parse(window.localStorage.getItem('links'));
      if (data) {
        links.value = [...data];
      }
    });

    return { links, copiedLink, createLink, handleCopy };
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  overflow-x: hidden;
}

body {
  font-size: 18px;
  font-family: 'Poppins', sans-serif;
  color: #9e9aa7;
  overflow-x: hidden;
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
  margin-bottom: 16px;
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

  &.btn-sm {
    padding: 8px 24px;
    font-size: 16px;
  }

  &.btn-dark {
    background-color: #3b3054;
  }
}

.main-area {
  background-color: rgba(59, 48, 84, 0.1);

  .link-list {
    margin-top: -50px; // To offset gap with form
    list-style: none;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;

    .link-item {
      width: 100%;
    }
  }
}

@media (max-width: 375px) {
  body {
    font-size: 16px;
  }

  .container {
    width: 100%;
    padding: 0 24px;
  }

  .h1 {
    font-size: 38px;
  }

  .h2 {
    font-size: 28px;
  }
}
</style>
