<template>
  <div class="main-layout">
    <div class="main-layout__header">
      <Header />
    </div>
    <div class="main-layout__content">
      <slot />
    </div>
    <div class="main-layout__footer">
      <Footer />
    </div>
  </div>
</template>
<script>
import Header from './Header.vue';
import Footer from './Footer.vue';

export default {
  name: "MainLayout",
  components: {
    Header,
    Footer,
  },
};
</script>
<style lang="scss">
  .main-layout {
    width: 100%;
  }
</style>
