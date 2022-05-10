<template>
  <div class="social-media">
    <a
      v-for="item in media"
      :key="item.name"
      target="_blank"
      :href="`https://www.${item.name}.com/`"
    >
      <img :src="require(`@/assets/${item.name}.svg`)" alt="img-facebook" />
    </a>
  </div>
</template>

<script>
export default {
  name: "SocialMedia",
  data() {
    return {
      media: [{ name: "facebook" }, { name: "linkedin" }, { name: "twitter" }],
    };
  },
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
