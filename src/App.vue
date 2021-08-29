<template>
  <div id="app">
    <GameMenu v-if="currentWindow === 1" @set-window="changeWindow" />

    <game
      v-if="currentWindow === 2"
      @add-points="addPoints"
      @set-window="changeWindow"
      :gamePoints="points"
      :cookie="cookieImage"
      :color="gameBackground"
      :cookieSpin="cookieSpin"
    />

    <shop
      v-if="currentWindow === 3"
      @set-window="changeWindow"
      @subtract-points="subtractPoints"
      @upgrade-points="pointsUpgrade"
      @change-bg="(color) => (this.gameBackground = color)"
      @new-cookie="(cookie) => (this.cookieImage = cookie)"
      @make-cookie-spin="cookieSpin = true"
      @start-helper="startHelper"
      :gamePoints="points"
      :bought="bought"
    />
  </div>
</template>

<script>
import GameMenu from "./components/GameMenu";
import game from "./components/game";
import shop from "./components/shop";
export default {
  components: {
    GameMenu,
    game,
    shop,
  },
  data() {
    return {
      currentWindow: 1,
      points: 0,
      pointsToAdd: 1,
      bought: [false, false, false, false, false, false, false],
      gameBackground: "darkseagreen",
      cookieSpin: false,
      cookieImage:
        "https://www.pngall.com/wp-content/uploads/2016/07/Cookie-PNG-Clipart.png",
    };
  },
  methods: {
    changeWindow(num) {
      this.currentWindow = num;
    },
    addPoints() {
      this.points += this.pointsToAdd;
    },
    subtractPoints(data) {
      this.points -= data.price;
      this.bought[data.boughtIndex] = true;
      this.currentWindow = 2;
    },
    pointsUpgrade(upgradeAmount) {
      this.pointsToAdd = upgradeAmount;
    },
    startHelper() {
      setInterval(() => this.points++, 1000);
    },
  },
};
</script>

<style>
* {
  margin: 0;
}
.window {
  height: 100vh;
  width: 100%;
  background-color: darkseagreen;
  display: flex;
  justify-content: center;
  align-items: center;
}
.spin {
  animation-name: spinAnimation;
  animation-duration: 3s;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
}
@keyframes spinAnimation {
  to {
    transform: rotate(360deg);
  }
}
</style>
