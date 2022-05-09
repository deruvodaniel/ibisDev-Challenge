<template>
  <div class="home-container">
    <GreenSection />
    <WhiteSection />
  </div>
</template>

<script>
import GreenSection from "../components/GreenSection.vue";
import WhiteSection from "../components/WhiteSection.vue";

export default {
  name: "HomeView",
  components: {
    GreenSection,
    WhiteSection,
  },
};
</script>

<style lang="scss">
// Global styles
@import "@/scss/_mixins.scss";
@import "@/scss/_commons.scss";

.home-container {
  height: fit-content;
  width: 100%;
}
</style>
