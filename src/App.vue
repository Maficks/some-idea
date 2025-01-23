<script setup>
import {ref, onMounted, watch} from 'vue';

const mouseX = ref(0);
const mouseY = ref(0);

const handleMouseMove = (event) => {
  mouseX.value = event.clientX;
  mouseY.value = event.clientY;
};

onMounted(() => {
  document.addEventListener('mousemove', handleMouseMove);
});

watch([mouseX, mouseY], () => {
  const xPos = (mouseX.value / window.innerWidth) * 100;
  const yPos = (mouseY.value / window.innerHeight) * 100;

  backgroundStyle.value = {
    ...backgroundStyle.value,
    backgroundPosition: `${xPos}% ${yPos}%`,
    transform: `scale(${1 + xPos / 500})`,
  };
});

const backgroundStyle = ref({
  background: 'linear-gradient(45deg, #ff6ec7, #ff8a00, #ff00ff, #00ffff)',
  backgroundSize: '400% 400%',
  animation: 'gradient-animation 10s ease infinite',
  transform: 'scale(1)',
  transition: 'transform 0.1s ease, background-position 0.1s ease',
});
</script>

<template>
  <div class="root">
    <div class="background-image"></div>
    <div class="background" :style="backgroundStyle"></div>
    <div class="content">
      <h1>You think it's funny to ask, HH?</h1>
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
.background-image {
  background: url("assets/1.jpeg") round;
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  opacity: 30%;
}
h1 {
  font-size: 3rem;
  margin: 20px 0;
  color: black;

}
.background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  background: linear-gradient(45deg, #ff6ec7, #ff8a00, #ff00ff, #00ffff);
  background-size: 400% 400%;
  animation: gradient-animation 10s ease infinite;
  transition: transform 0.1s ease, background-position 0.1s ease;
}
@keyframes gradient-animation {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
</style>
