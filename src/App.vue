<template>
  <div id="app">
    <HomeView />
  </div>
</template>

<script>
import HomeView from "./components/HomeView.vue";

export default {
  name: "App",
  components: {
    HomeView,
  },
};
</script>

<style lang="scss">
// Global styles
@import "@/scss/main.scss";

#app {
  font-family: $fontMain;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
