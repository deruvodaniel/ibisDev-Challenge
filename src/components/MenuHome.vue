<template>
  <div class="menu">
    <span></span>
    <span></span>
    <span></span>
  </div>
</template>

<script>
export default {
  name: "MenuHome",
};
</script>

<style lang="scss">
// Global styles
@import "@/scss/_mixins.scss";
@import "@/scss/_commons.scss";

.menu {
  position: absolute;
  top: 49px;
  left: 30px;
  height: 57px;
  width: 57px;
  background-color: $secondaryColor;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  animation-name: img-animation;
  animation-duration: 1.5s;
  animation-iteration-count: 1;
  span {
    background: $mainColor;
    width: 32px;
    min-height: 3px;
    margin: 2px;
    border-radius: 3px;
    &:last-child,
    &:first-child {
      width: 19px;
    }
  }
  @keyframes img-animation {
    0% {
      transform: translateX(100px);
      opacity: 0;
    }
    100% {
      transform: translateX(0px);
      opacity: 1;
    }
  }
}
</style>
