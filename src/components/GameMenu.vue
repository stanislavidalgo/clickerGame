<template>
  <div class="window">
    <div class="startGame" @click="$emit('set-window', 2)">Start Game</div>
  </div>
</template>

<script>
export default {
  name: "GameMenu"
}
</script>

<style scoped>
.startGame {
  padding: 20px;
  font-size: 30px;
  background-color: #588558;
  color: white;
  font-weight: 900;
  cursor: pointer;
}
</style>