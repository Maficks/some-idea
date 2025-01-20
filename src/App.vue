<script setup>
import { ref, onMounted } from 'vue';

const mouseX = ref(0);
const mouseY = ref(0);

const handleMouseMove = (event) => {
  mouseX.value = event.clientX;
  mouseY.value = event.clientY;
};

onMounted(() => {
  document.addEventListener('mousemove', handleMouseMove);
});
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
.root {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>
