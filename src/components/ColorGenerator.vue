<script setup>
import { ref } from 'vue';

const numberOfBoxes = 7;
const boxColors = ref(Array.from({ length: numberOfBoxes }, () => getRandomHexColor()));

function changeColors() {
  boxColors.value = Array.from({ length: numberOfBoxes }, () => getRandomHexColor());
}

function getRandomHexColor() {
  const letters = '0123456789abcdef';
  let color = '#';
  for (let i = 1; i <= 6; i++) {
    color += letters[Math.floor(Math.random() * 16)];
  }
  return color;
}
</script>

<template>
  <div>
    <div class="color-row">
      <div v-for="(color, position) in boxColors" :style="{ backgroundColor: color }" class="color-box" :key="position"></div>
    </div>
    <div class="color-row">
      <p v-for="(color, position) in boxColors" :key="position" class="hex-text">Hex: {{ color }}</p>
    </div>
    
    <button @click="changeColors">Genereaza alte culori</button>
    
  </div>
</template>

<style scoped>
.color-row {
  display: flex;
}

.color-box {
  flex: 1;
  height: 6rem;
  width: 6rem;
  margin-right: 1.3rem; 
}

.hex-text {
  margin-right: 1.875rem;
}

button {
  margin-top: 1rem; 
}
</style>