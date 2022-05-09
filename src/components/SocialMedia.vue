<template>
  <div class="social-media">
    <a href="https://www.facebook.com/">
      <img src="../assets/facebook.svg" alt="img-facebook" />
    </a>
    <a href="https://twitter.com/">
      <img src="../assets/linkedin.svg" alt="img-linkedin" />
    </a>
    <a href="">
      <img src="../assets/twitter.svg" alt="img-twitter" />
    </a>
  </div>
</template>

<script>
export default {
  name: "SocialMedia",
};
</script>

<style lang="scss">
// Global styles
@import "@/scss/_mixins.scss";
@import "@/scss/_commons.scss";

.social-media {
  width: 86px;
  height: 21px;
  margin-top: 33px;
  display: flex;
  justify-content: space-between;
  animation-name: media-animation;
  animation-duration: 1.5s;
  animation-iteration-count: 1;
  a {
    img {
      height: 21px;
      width: 21px;
    }
  }
}
@include animation-vertical(media-animation, 600px, 0px);
</style>
