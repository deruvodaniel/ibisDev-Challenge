<template>
  <section class="green-section">
    <MenuHome
      ref="toogler"
      :class="{ menu: menuOpen }"
      @click.prevent="handleToogleMenu()"
      @blur="close()"
    />
    <div v-show="menuOpen" class="popover" ref="popover">
      <a @click.stop="handleToogleMenu()" href="#">Home</a>
      <a @click.stop="handleToogleMenu()" href="#white">Esperiences</a>
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
          the 1500s, when an unknown printer took a galley of type and scrambled
          it to make a type specimen book. It has survived not only five
          centuries, but also the leap into electronic typesetting, remaining
          essentially unchanged. It was pop</span
        >
        <span v-show="homeText === 2"
          >is simply dummy text of the printing and typesetting industry. Lorem
          Ipsum has been the industry's standard dummy text ever since the
          1500s, when an unknown printer took a galley of type and scrambled it
          to make a type specimen book.</span
        >
        <span v-show="homeText === 3"
          >Vestibulum sit amet odio eget mauris volutpat vulputate. Cras ac
          vulputate nibh, vel faucibus turpis. Integer condimentum eget odio
          eget euismod. Nam pulvinar justo diam, aliquet posuere orci euismod
          sed. Mauris vitae mattis nibh. Cras condimentum vehicula tempor. Donec
          consequat varius mattis. Pellentesque in venenatis est, et venenatis
          justo. Cras posuere sem ex, quis vehicula dui vestibulum et. Sed in
          rhoncus risus.
        </span>
      </div>
      <SocialMedia />
    </div>
    <div class="arrow-handlers">
      <div @click="handleChangeImg('next')" class="arrow-container left-arrow">
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
</template>

<script>
import MenuHome from "../components/MenuHome.vue";
import SocialMedia from "../components/SocialMedia.vue";

export default {
  name: "GreenSection",
  components: {
    MenuHome,
    SocialMedia,
  },

  data() {
    return {
      homeImage: 1,
      homeText: 1,
      menuOpen: false,
    };
  },

  beforeDestroy() {
    document.removeEventListener("click", this.close);
  },

  methods: {
    handleToogleMenu() {
      this.$refs.popover.style.opacity = "1";
      this.menuOpen = !this.menuOpen;
    },

    close(event) {
      if (event.target !== this.$refs.toogler.$el) {
        if (!this.$refs.popover.contains(event.target)) {
          this.menuOpen = false;
        }
      }
    },

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
};
</script>

<style lang="scss">
// Global styles
@import "@/scss/_mixins.scss";
@import "@/scss/_commons.scss";

.green-section {
  background-color: $secondaryColor;
  color: $mainColor;
  padding-bottom: 55px;
  .menu {
    &:hover {
      cursor: pointer;
      opacity: 0.9;
    }
  }
  .popover {
    position: absolute;
    top: 75px;
    left: 100px;
    background-color: $secondaryColor;
    width: 180px;
    height: 150px;
    display: flex;
    flex-direction: column;
    transition: all ease 1s;
    opacity: 0;
    a {
      display: flex;
      align-items: center;
      justify-content: center;
      text-decoration: none;
      font-size: $textS;
      height: 50%;
      color: $mainColor;
      font-weight: 600;
      &:hover {
        background-color: $mainColor;
        color: $secondaryColor;
        transition: all ease 1s;
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
  }
  .hero {
    padding: 72px $padding30 $padding30 $padding30;
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
        font-size: $testXs;
        animation-name: span-animation;
        animation-duration: 1s;
        animation-iteration-count: 1;
      }
      @include animation-vertical(span-animation, 200px, 0px);
    }
    @include animation-vertical(div-animation, 200px, 0px);
    @include animation-vertical(header-animation, 200px, 0px);
  }
  .arrow-handlers {
    position: absolute;
    top: 432px;
    right: 20px;
    .left-arrow {
      margin-right: 20px;
      animation-name: arrow-left-animation;
      animation-duration: 1.5s;
      animation-iteration-count: 1;
      @keyframes arrow-left-animation {
        0% {
          transform: translateY(600px);
        }
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
        0% {
          transform: translateY(600px);
        }
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

@include mediumScreen {
  .green-section {
    height: 100vh;
  }
}

@include desktopScreen {
  .green-section {
    display: flex;
    flex-direction: row-reverse;
    height: 100vh;
    padding: 0;
    .popover {
      left: auto;
      right: 120px;
    }
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
      width: 56%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 0 100px;
      h1 {
        font-size: $textL;
        padding-bottom: 41px;
      }
      span {
        font-size: $testXs;
        padding-top: 39px;
      }
    }
  }
}
</style>
