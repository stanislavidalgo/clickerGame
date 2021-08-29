<template>
<div class="window">
  <div class="back" @click="$emit('set-window', 2)">Back</div>
  <div v-if="!bought[0]"
       @click="counterUpgrades(0, 2, 100)"
       class="back">2x Click (price 100$) </div>
  <div v-if="!bought[1]"
       @click="counterUpgrades(1, 5, 500)"
       class="back">5x Click (price 500$) </div>
  <div v-if="!bought[2]"
       @click="counterUpgrades(2, 10, 1000)"
       class="back">10x Click (price 1000$ </div>

  <div v-if="!bought[3]" @click="backgroundUpgrade(3, 300)"
       class="back">new background (price 300$ </div>

  <div v-if="!bought[4]"
       @click="cookieUpgrade(4, 200)"
       class="back">new cookie (price 200$ </div>

  <div v-if="!bought[5]"
       @click="cookieSpinUpgrade(5, 400)"
       class="back">cookie spin (price 400$) </div>

  <div v-if="!bought[6]"
       @click="helperUpgrade(6, 600)"
       class="back">helper (600$) </div>

</div>
</template>

<script>
export default {
name: "shop",
  props: ['gamePoints', "bought"],
  methods: {
    counterUpgrades(boughtIndex, counter, price) {
      if(this.gamePoints >= price ) {
        this.$emit('subtract-points', {price, boughtIndex})
        this.$emit('upgrade-points', counter)
      }
    },
    backgroundUpgrade(boughtIndex, price) {
      if(this.gamePoints >= price ) {
        this.$emit('subtract-points', {price, boughtIndex})
        this.$emit('change-bg', '#5C99CD')
      }
    },
    cookieUpgrade(boughtIndex, price) {
      if(this.gamePoints >= price ) {
        this.$emit('subtract-points', {price, boughtIndex})
        this.$emit('new-cookie', 'http://assets.stickpng.com/thumbs/5cb77529a7c7755bf004c101.png')
      }
    },
    cookieSpinUpgrade(boughtIndex, price) {
      if(this.gamePoints >= price ) {
        this.$emit('subtract-points', {price, boughtIndex})
        this.$emit('make-cookie-spin')
      }
    },
    helperUpgrade(boughtIndex, price) {
      if(this.gamePoints >= price ) {
        this.$emit('subtract-points', {price, boughtIndex})
        this.$emit('start-helper')
      }
    },
  }
}
</script>

<style scoped>
.back {
  padding: 20px;
  font-size: 30px;
  background-color: #588558;
  color: white;
  font-weight: 900;
  cursor: pointer;
  margin: 10px;
}
.window {
  flex-direction: column;
}
</style>