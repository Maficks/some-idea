<script setup>
import { ref } from 'vue';

const mouseX = ref(0);
const mouseY = ref(0);

// Функция для отслеживания положения мыши
const handleMouseMove = (event) => {
  mouseX.value = event.clientX;
  mouseY.value = event.clientY;
};
</script>

<template>
  <div class="root">
    <div class="background-image"></div>
    <div class="background"></div>
    <div class="content">

    </div>
  </div>
</template>

<style scoped>

</style>
