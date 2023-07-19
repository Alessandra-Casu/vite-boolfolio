<script>
import AppNav from "./components/AppNav.vue";
import AppFooter from "./components/AppFooter.vue";

export default {
  components: {
    AppNav,
    AppFooter,
  },
};
</script>

<template>
  <AppNav />

  <div class="container">
    <router-view></router-view>
  </div>

  <AppFooter />
</template>

<style lang="scss">
@import "bootstrap/scss/bootstrap";
</style>
