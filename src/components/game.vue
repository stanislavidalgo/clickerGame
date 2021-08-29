<template>
  <div class="window" :style="{backgroundColor: color}">
    <div class="shop" @click="$emit('set-window', 3)">Shop</div>

    <div class="cookieScale">
      <img :class="{spin: cookieSpin}" @click="$emit('add-points')"
           :src="cookie" alt="">
    </div>

    <h1>Pints: {{ gamePoints }}</h1>
  </div>
</template>

<script>
export default {
name: "game",
  props: ['gamePoints', 'color', 'cookie', 'cookieSpin']
}
</script>

<style scoped>
.shop {
  padding: 20px;
  font-size: 30px;
  background-color: #588558;
  color: white;
  font-weight: 900;
  cursor: pointer;
  margin-bottom: 50px;
}
.cookieScale:hover {
  transform: scale(1.1);
  cursor: pointer;
}
.window {
  flex-direction: column;
}
h1 {
  padding: 50px;
}
</style>