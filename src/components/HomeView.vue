/* eslint-disable prettier/prettier */
<template>
  <div class="home-container">
    <section class="green-section">
      <div class="menu">
        <span></span>
        <span></span>
        <span></span>
      </div>
      <div
        class="image-container"
        ref="imageContainer"
        :style="{
          'background-image':
            'url(' + require(`@/assets/home-${this.homeImage}.jpg`) + ') ',
        }"
      ></div>
      <div ref="heroRef" class="hero">
        <h1 v-show="homeText === 1">Crea un impacto positivo</h1>
        <h1 v-show="homeText === 2">Elige tu próximo destino</h1>
        <h1 v-show="homeText === 3">Encuentra la inspiracíon</h1>
        <div class="border-wrapper">
          <span v-show="homeText === 1"
            >Lorem Ipsum has been the industry’s standard dummy text ever since
            the 1500s, when an unknown printer took a galley of type and
            scrambled it to make a type specimen book. It has survived not only
            five centuries, but also the leap into electronic typesetting,
            remaining essentially unchanged. It was pop</span
          >
          <span v-show="homeText === 2"
            >Lorem Ipsum has been the industry’s standard dummy text ever since
            the 1500s, when an unknown printer took a galley of type and
            scrambled it to make a type specimen book. It has survived not only
            five centuries, but also the leap into electronic typesetting,
            remaining essentially unchanged. It was pop</span
          >
          <span v-show="homeText === 3"
            >Lorem Ipsum has been the industry’s standard dummy text ever since
            the 1500s, when an unknown printer took a galley of type and
            scrambled it to make a type specimen book. It has survived not only
            five centuries, but also the leap into electronic typesetting,
            remaining essentially unchanged. It was pop</span
          >
        </div>
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
      </div>
      <div class="arrow-handlers">
        <div
          @click="handleChangeImg('next')"
          class="arrow-container left-arrow"
        >
          <img src="../assets/chevron.svg" alt="arrow-icon" />
        </div>
        <div
          @click="handleChangeImg('previous')"
          class="arrow-container right-arrow"
        >
          <img src="../assets/chevron.svg" alt="arrow-icon" />
        </div>
      </div>
    </section>
    <section class="white-section">
      <div class="header">
        <h2>Hay un mundo</h2>
        <span>enorme</span>
      </div>
      <div class="color-img-wrapper"></div>
      <div class="green-wrapper">
        <div class="green-background"></div>
      </div>
      <div class="experiences">
        <div class="item">
          <img src="../assets/icon1.svg" alt="world-icon" />
          <div class="text-wrapper">
            <h3>Unforgettable experiences</h3>
            <span
              >Creating your trip is entirely collaborative and our Travel
              Researchers are here for every step.</span
            >
          </div>
        </div>
        <div class="item">
          <img src="../assets/icon2.svg" alt="rudder-icon" />
          <div class="text-wrapper">
            <h3>Unforgettable experiences</h3>
            <span
              >Creating your trip is entirely collaborative and our Travel
              Researchers are here for every step.</span
            >
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "HomeView",
  props: {
    msg: String,
  },
  data() {
    return {
      homeImage: 1,
      homeText: 1,
    };
  },

  methods: {
    handleChangeImg(toogle) {
      if (toogle === "next") {
        this.homeImage++;
        this.homeText++;
        if (this.homeImage > 3) {
          this.homeImage = 1;
          this.homeText = 1;
        }
      } else if (toogle === "previous") {
        this.homeImage--;
        this.homeText--;
        if (this.homeImage < 1) {
          this.homeImage = 3;
          this.homeText = 3;
        }
      }
    },
  },

  watch: {
    homeImage() {
      this.$refs.heroRef.style.opacity = "";
    },
  },
};
</script>

<style lang="scss">
// Global styles
@import "@/scss/main.scss";

.home-container {
  .green-section,
  .white-section {
    height: fit-content;
    width: 100%;
  }
  .green-section {
    background-color: $secondaryColor;
    color: $mainColor;
    padding-bottom: 55px;
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
      @keyframes span-animation {
        0% {
          transform: translateX(100px);
          opacity: 0;
        }
        100% {
          transform: translateY(0px);
          opacity: 1;
        }
      }
    }
    .image-container {
      width: auto;
      height: 482px;
      display: flex;
      overflow-x: hidden;
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
      animation-name: img-animation;
      animation-duration: 1s;
      animation-iteration-count: 1;
    }
    @keyframes img-animation {
      0% {
        transform: translateX(500px) scale(2);
        opacity: 0;
      }
      100% {
        transform: translateX(0px) scale(1);
        opacity: 1;
      }
    }
    .hero {
      padding: 72px 30px 30px 30px;
      h1 {
        font-size: 35px;
        padding-bottom: 12px;
        font-weight: 900;
        animation-name: header-animation;
        animation-duration: 0.7s;
        animation-iteration-count: 1;
      }
      .border-wrapper {
        border-top: 5px solid $mainColor;
        padding-top: 26px;
        animation-name: div-animation;
        animation-duration: 1s;
        animation-iteration-count: 1;
        span {
          line-height: 45px;
          font-size: 16px;
          animation-name: span-animation;
          animation-duration: 1s;
          animation-iteration-count: 1;
        }
        @keyframes span-animation {
          0% {
            transform: translateY(200px);
            opacity: 0;
          }
          100% {
            transform: translateY(0px);
            opacity: 1;
          }
        }
      }
      @keyframes div-animation {
        0% {
          transform: translateY(200px);
          opacity: 0;
        }
        100% {
          transform: translateY(0px);
          opacity: 1;
        }
      }
      @keyframes header-animation {
        0% {
          transform: translateY(200px);
          opacity: 0;
        }
        100% {
          transform: translateY(0px);
          opacity: 1;
        }
      }
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
      @keyframes media-animation {
        30% {
          transform: translateY(600px);
          opacity: 0;
        }
        100% {
          transform: translateY(0px);
          opacity: 1;
        }
      }
    }
    .arrow-handlers {
      position: absolute;
      top: 432px;
      right: 20px;
      .arrow-container {
        width: 50px;
        height: 50px;
        background-color: $mainColor;
        display: flex;
        align-items: center;
        justify-content: center;
        &:hover {
          cursor: pointer;
          opacity: 0.8;
        }
        img {
          width: 21px;
          height: 13px;
        }
      }
      .left-arrow {
        margin-right: 20px;
        animation-name: arrow-left-animation;
        animation-duration: 1.5s;
        animation-iteration-count: 1;
        @keyframes arrow-left-animation {
          30% {
            transform: translateY(600px);
          }
          100% {
            transform: translateY(0px);
          }
        }
        img {
          transform: rotate(90deg);
        }
      }
      .right-arrow {
        position: absolute;
        right: 100%;
        animation-name: arrow-right-animation;
        animation-duration: 1.7s;
        animation-iteration-count: 1;
        @keyframes arrow-right-animation {
          50% {
            transform: translateY(600px);
          }
          100% {
            transform: translateY(0px);
          }
        }
        img {
          transform: rotate(270deg);
        }
      }
    }
  }
  .white-section {
    background-color: $mainColor;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    .header {
      padding: 30px;
      color: $secondaryColor;
      width: 70%;
      text-align: left;
      h2 {
        font-size: 30px;
        font-weight: 900;
      }
      span {
        text-transform: uppercase;
        letter-spacing: 22px;
        width: 100%;
        font-size: 30px;
        font-weight: 900;
        text-align: right;
        float: right;
      }
    }
    .color-img-wrapper {
      position: relative;
      margin: 0 auto;
      top: 120px;
      z-index: 2;
      width: 350px;
      height: 296px;
      background-image: url("../assets/color.jpg");
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
    }
    .green-wrapper {
      height: 240px;
      position: relative;
      top: -150px;
      display: flex;
      justify-content: center;
      align-items: center;
      .green-background {
        width: 265px;
        height: 450px;
        margin: 0 auto;
        background-image: url("../assets/green.jpg");
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
      }
    }
    .experiences {
      padding: 30px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      .item {
        display: flex;
        margin-bottom: 40px;
        .text-wrapper {
          padding-left: 23px;
          color: $secondaryColor;
          h3 {
            font-size: 18px;
            font-weight: 600;
          }
          span {
            font-size: 16px;
            line-height: 32px;
          }
        }
      }
    }
  }
}

@include mediumScreen {
  .home-container {
    .green-section {
      height: 100vh;
    }
    .white-section {
      height: 100vh;
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      grid-template-rows: repeat(8, 1fr);
      grid-column-gap: 0px;
      grid-row-gap: 0px;
      .header {
        grid-area: 2 / 4 / 4 / 12;
        text-align: right;
        width: 100%;
        z-index: 2;
        padding: 0;
        h2 {
          font-size: 50px;
          padding-right: 50px;
        }
        span {
          font-size: 80px;
          letter-spacing: 50px;
        }
      }
      .green-wrapper {
        grid-area: 2 / 2 / 8 / 6;
        top: auto;
        .green-background {
          width: 425px;
          height: 724px;
        }
      }
      .color-img-wrapper {
        top: auto;
        grid-area: 4 / 3 / 8 / 7;
        width: 446px;
        height: 342px;
      }
      .experiences {
        grid-area: 4 / 7 / 8 / 12;
        padding-right: 0;
      }
    }
  }
}

@include desktopScreen {
  .home-container {
    .green-section {
      display: flex;
      flex-direction: row-reverse;
      height: 100vh;
      padding: 0;
      .arrow-handlers {
        top: auto;
        bottom: 70px;
        left: 56%;
      }
      .menu {
        left: auto;
        right: 53px;
      }
      .image-container {
        min-width: 44%;
        height: 100vh;
      }
      .hero {
        width: 56%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        padding: 0 100px;
        h1 {
          font-size: 60px;
          padding-bottom: 41px;
        }
        span {
          font-size: 16px;
          padding-top: 39px;
        }
      }
    }
    .white-section {
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      grid-template-rows: repeat(12, 1fr);
      grid-column-gap: 0px;
      grid-row-gap: 0px;
      .header {
        grid-area: 3 / 4 / 5 / 12;
        h2 {
          font-size: 71px;
          padding-right: 75px;
        }
        span {
          font-size: 102px;
          letter-spacing: 75.48px;
        }
      }
      .green-wrapper {
        grid-area: 2 / 2 / 12 / 6;
      }
      .color-img-wrapper {
        grid-area: 6 / 4 / 11 / 8;
      }
      .experiences {
        grid-area: 6 / 8 / 11 / 12;
        h3 {
          font-size: 18px;
        }
        span {
          font-size: 16px;
        }
      }
    }
  }
}
</style>
