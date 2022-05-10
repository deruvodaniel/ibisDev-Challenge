<template>
  <div @click="handleClick" class="go-up-button">
    <div class="arrow-container">
      <img src="../assets/chevron.svg" alt="arrow-icon" />
    </div>
  </div>
</template>

<script>
export default {
  name: "GoUpButton",

  methods: {
    handleClick(event) {
      this.$emit("click", event);
    },
  },
};
</script>

<style lang="scss">
// Global styles
@import "@/scss/_mixins.scss";
@import "@/scss/_commons.scss";

.go-up-button {
  display: none;
  position: absolute;
  bottom: -95%;
  right: 53px;
  .arrow-container {
    &:hover {
      filter: saturate(30%);
      filter: drop-shadow(2px 2px 2px $secondaryColor);
    }
  }
}

@include desktopScreen {
  .go-up-button {
    display: block;
  }
}
</style>
