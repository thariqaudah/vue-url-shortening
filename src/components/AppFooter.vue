<template>
  <footer class="app-footer">
    <div class="container">
      <div class="logo">
        <img src="../assets/logo-light.svg" alt="Logo" />
      </div>
      <nav class="navigation">
        <p class="navigation-title">Features</p>
        <ul class="navigation-list">
          <li><a href="#" class="link">Link Shortening</a></li>
          <li><a href="#" class="link">Branded Links</a></li>
          <li><a href="#" class="link">Analytics</a></li>
        </ul>
      </nav>
      <nav class="navigation">
        <p class="navigation-title">Resources</p>
        <ul class="navigation-list">
          <li><a href="#" class="link">Blog</a></li>
          <li><a href="#" class="link">Developers</a></li>
          <li><a href="#" class="link">Support</a></li>
        </ul>
      </nav>
      <nav class="navigation">
        <p class="navigation-title">Company</p>
        <ul class="navigation-list">
          <li><a href="#" class="link">About</a></li>
          <li><a href="#" class="link">Our Team</a></li>
          <li><a href="#" class="link">Careers</a></li>
          <li><a href="#" class="link">Contact</a></li>
        </ul>
      </nav>
      <nav class="navigation socials">
        <ul class="navigation-list">
          <li>
            <a href="#" class="link">
              <i class="fab fa-facebook-square"></i>
            </a>
          </li>
          <li>
            <a href="#" class="link">
              <i class="fab fa-twitter"></i>
            </a>
          </li>
          <li>
            <a href="#" class="link">
              <i class="fab fa-pinterest"></i>
            </a>
          </li>
          <li>
            <a href="#" class="link">
              <i class="fab fa-instagram"></i>
            </a>
          </li>
        </ul>
      </nav>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'AppFooter',
};
</script>

<style lang="scss" scoped>
.app-footer {
  padding: 64px 0;
  background-color: #232127;

  .container {
    display: grid;
    grid-template-columns: 2fr repeat(4, 1fr);
    gap: 32px;

    @media (max-width: 375px) {
      grid-template-columns: 1fr;
      text-align: center;

      .logo {
        margin-bottom: 32px;
      }
    }
  }

  .navigation {
    .navigation-title {
      font-size: 16px;
      font-weight: 500;
      color: #fff;
      margin-bottom: 16px;
    }
    .navigation-list {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 4px;

      .link {
        font-size: 14px;
        text-decoration: none;
        color: #bfbfbf;
        transition: all 0.3s ease-out;

        &:hover,
        &:active {
          color: #2acfcf;
        }
      }
    }

    &.socials .navigation-list {
      flex-direction: row;
      gap: 16px;

      @media (max-width: 375px) {
        justify-content: center;
      }

      .link {
        font-size: 24px;
      }
    }
  }
}
</style>
