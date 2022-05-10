<template>
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
</template>

<script>
export default {
  name: "WhiteSection",
};
</script>

<style lang="scss">
// Global styles
@import "@/scss/main.scss";

.white-section {
  background-color: $mainColor;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  .header {
    padding: $padding30;
    color: $secondaryColor;
    width: 70%;
    text-align: left;
    h2 {
      font-size: $textM;
      font-weight: 900;
    }
    span {
      text-transform: uppercase;
      letter-spacing: 22px;
      width: 100%;
      font-size: $textM;
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
          font-size: $testXs;
          line-height: 32px;
        }
      }
    }
  }
}

@include mediumScreen {
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
        font-size: $textXl;
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
      max-width: 446px;
      min-width: auto;
      height: 342px;
    }
    .experiences {
      grid-area: 4 / 7 / 8 / 12;
      padding-right: 0;
      .text-wrapper {
        min-width: 195px;
      }
    }
  }
}

@include desktopScreen {
  .white-section {
    height: 100vh;
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
        font-size: $testXs;
      }
    }
  }
}
</style>
