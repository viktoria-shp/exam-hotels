<template>
  <footer id="footer" class="footer">
    <div class="footer__box container">
      <p class="footer__text">{{ title }}</p>
      <div class="footer__links">
        <a
          class="footer__link"
          v-for="(link, index) in links"
          :key="index"
          :href="links.link"
        >
          <img :src="link.iconSrc" alt="img" class="footer__icon" />
        </a>
      </div>
    </div>
  </footer>
</template>
<script>
export default {
  name: "Footer",
  data() {
    return {
      title: "©2014 tulusdriyo. All Rights Reserved.",
      links: [
        {
          link: "https://google.com",
          iconSrc: require("@/assets/behance.svg"),
        },
        {
          link: "https://google.com",
          iconSrc: require("@/assets/linked-in.svg"),
        },
        {
          link: "https://google.com",
          iconSrc: require("@/assets/google.svg"),
        },
        {
          link: "https://google.com",
          iconSrc: require("@/assets/facebook.svg"),
        },
        {
          link: "https://google.com",
          iconSrc: require("@/assets/twitter.svg"),
        },
      ],
    };
  },
};
</script>
<style lang="scss">
.footer {
  display: flex;
  justify-content: center;
  padding: 83px 0 86px;
  background: #9f9acf;
  @include media-max-width($screen-tablet) {
    padding: 25px 10px;
  }
  &__text {
    font-size: 18px;
    color: white;
    font-family: "PT Sans", sans-serif;
    font-weight: bold;
    @include media-max-width($screen-tablet) {
      font-size: 12px;
    }
  }
  &__links {
    display: flex;
  }
  &__link {
    margin-right: 24px;
    @include media-max-width($screen-tablet) {
      margin-right: 15px;
    }
  }
  &__icon {
    @include media-max-width($screen-tablet) {
      width: 25px;
    }
  }
  &__link:last-child {
    margin-right: 0;
  }
  &__box {
    display: flex;
    justify-content: space-between;
    @include media-max-width($screen-tablet-small) {
      flex-direction: column;
      align-items: center;
    }
  }
}
</style>
