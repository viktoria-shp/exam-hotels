<template>
  <div class="app">
    <main-layout>
      <router-view />
    </main-layout>
  </div>
</template>
<script>
import MainLayout from "./components/layout/MainLayout.vue";

export default {
  components: {
    MainLayout,
  },
};
</script>

<style lang="scss">
.app {
  min-height: 100vh;
  display: flex;
  background-color: var(--bg-color);
  color: var(--text-color);
}
a {
  color: inherit;
}
</style>
