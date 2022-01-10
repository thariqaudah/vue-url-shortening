<template>
  <div class="boost-section">
    <div class="container">
      <h2 class="h2">Boost your links today</h2>
      <a href="#" class="btn btn-rounded">Get Started</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BoostSection',
};
</script>

<style lang="scss" scoped>
.boost-section {
  text-align: center;
  background-color: #3b3054;
  background-image: url('../assets/bg-boost-desktop.svg');
  background-repeat: no-repeat;
  background-size: cover;
  padding: 64px 0;

  @media (max-width: 375px) {
    background-image: url('../assets/bg-boost-mobile.svg');
  }

  .h2 {
    color: #fff;
  }
}
</style>
