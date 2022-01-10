<template>
  <div class="statistics-section">
    <div class="container">
      <div class="header">
        <h2 class="h2">Advanced Statistics</h2>
        <p>
          Track how your links are performing across the web with our advanced
          statistics dashboard.
        </p>
      </div>

      <div class="cards">
        <div class="card">
          <div class="card-icon">
            <img src="../assets/icon-brand-recognition.svg" alt="" />
          </div>
          <p class="card-title">Brand Recognition</p>
          <p class="card-description">
            Boost your brand recognition with each click. Generic links don’t
            mean a thing. Branded links help instil confidence in your content.
          </p>
        </div>
        <div class="card">
          <div class="card-icon">
            <img src="../assets/icon-detailed-records.svg" alt="" />
          </div>
          <p class="card-title">Detailed Records</p>
          <p class="card-description">
            Gain insights into who is clicking your links. Knowing when and
            where people engage with your content helps inform better decisions.
          </p>
        </div>
        <div class="card">
          <div class="card-icon">
            <img src="../assets/icon-fully-customizable.svg" alt="" />
          </div>
          <p class="card-title">Fully Customizable</p>
          <p class="card-description">
            Improve brand awareness and content discoverability through
            customizable links, supercharging audience engagement.
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'StatisticsSection',
};
</script>

<style lang="scss" scoped>
.statistics-section {
  padding: 96px 0 200px 0;

  @media (max-width: 375px) {
    padding-bottom: 96px;
  }

  .header {
    width: 40%;
    margin: 0 auto;
    text-align: center;
    margin-bottom: 100px;

    @media (max-width: 375px) {
      width: 100%;
    }

    p {
      color: #9e9aa7;
      font-size: 18px;
      line-height: 1.6;

      @media (max-width: 375px) {
        font-size: 16px;
      }
    }
  }

  .cards {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 32px;

    @media (max-width: 375px) {
      grid-template-columns: 1fr;
      gap: 96px;
    }

    .card {
      background-color: #fff;
      padding: 80px 48px 48px 48px;
      border-radius: 9px;
      position: relative;
      z-index: 100;

      @media (max-width: 375px) {
        padding: 72px 32px 32px 32px;
        text-align: center;
      }

      &:nth-child(2) {
        transform: translateY(15%);

        @media (max-width: 375px) {
          transform: translateY(0);
        }

        &::before,
        &::after {
          content: '';
          display: block;
          width: 32px;
          height: 8px;
          background-color: #2acfcf;
          position: absolute;

          @media (max-width: 375px) {
            width: 8px;
            height: 96px;
          }
        }

        &::before {
          left: 0;
          top: 35%;
          transform: translateX(-100%);

          @media (max-width: 375px) {
            top: 0;
            left: 50%;
            transform: translate(-50%, -100%);
          }
        }

        &::after {
          right: 0;
          top: 35%;
          transform: translateX(100%);

          @media (max-width: 375px) {
            top: 100%;
            right: 50%;
            transform: translateX(50%);
          }
        }
      }

      &:nth-child(3) {
        transform: translateY(30%);

        @media (max-width: 375px) {
          transform: translateY(0);
        }
      }

      .card-icon {
        display: inline-block;
        width: 80px;
        height: 80px;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 50%;
        background-color: #3b3054;
        position: absolute;
        top: 0;
        transform: translateY(-50%);

        @media (max-width: 375px) {
          left: 50%;
          transform: translate(-50%, -50%);
        }
      }

      .card-title {
        font-size: 24px;
        font-weight: 700;
        color: #35323e;
        line-height: 1.2;
        margin-bottom: 16px;
      }

      .card-description {
        font-size: 18px;
        left: 1.8;

        @media (max-width: 375px) {
          font-size: 16px;
        }
      }
    }
  }
}
</style>
