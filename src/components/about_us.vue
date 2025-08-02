<template>
  <v-container class="custom-starry-bg overflow-y-auto fill-height" max-width="900">
    <v-btn icon class="back-button" @click="$router.push({ name: 'Home' })">
      <v-icon>mdi-arrow-left</v-icon>
    </v-btn>

    <!-- Estrelas -->
    <div
      v-for="(star, index) in stars"
      :key="'star-' + index"
      class="star"
      :style="{
        top: `${star.top}%`,
        left: `${star.left}%`,
        animationDuration: `${star.duration}s`
      }"
    ></div>

    <!-- Lua -->
    <div class="moon"></div>

    <cards />
    <spoiler />
  </v-container>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import spoiler from './spoiler.vue'
import cards from './cards.vue'

const stars = ref([])

onMounted(() => {
  const totalStars = 150
  stars.value = Array.from({ length: totalStars }, () => ({
    top: Math.random() * 100,
    left: Math.random() * 100,
    duration: 1 + Math.random() * 2
  }))
})
</script>

<style scoped>
.custom-starry-bg {
  background: radial-gradient(ellipse at bottom, #0b1d3a 0%, #050d1a 100%);
  overflow: hidden;
  position: relative;
  border-radius: 12px;
  padding-top: 60px;
}

.back-button {
  position: absolute;
  top: 10px;
  left: 10px;
  color: white;
}

/* Estilo centralizado */
.book-title-wrapper {
  width: 100%;
  text-align: center;
  margin: 60px auto 20px;
}

.book-title {
  display: inline-block;
  font-family: 'Georgia', serif;
  font-size: 3.5rem;
  color: #f9d47d;
  padding: 20px 40px;
  border: 2px solid #f9d47d;
  border-radius: 12px;
  background: rgba(255, 255, 255, 0.05);
  letter-spacing: 3px;
  text-shadow: 2px 2px 6px #000;
  box-shadow: 0 0 15px rgba(249, 212, 125, 0.4);
  animation: glowTitle 3s ease-in-out infinite;
}

.ornament {
  font-size: 1.5rem;
  color: #f9d47d;
  text-shadow: 0 0 10px #000;
  margin-bottom: 8px;
}

@keyframes glowTitle {
  0%, 100% {
    box-shadow: 0 0 15px rgba(249, 212, 125, 0.4);
  }
  50% {
    box-shadow: 0 0 30px rgba(249, 212, 125, 0.7);
  }
}

.star {
  position: absolute;
  width: 2px;
  height: 2px;
  background: white;
  border-radius: 50%;
  opacity: 0.8;
  animation: twinkle ease-in-out infinite;
}

@keyframes twinkle {
  0%, 100% { opacity: 0.2; }
  50% { opacity: 1; }
}

.moon {
  position: absolute;
  top: 30px;
  right: 40px;
  width: 80px;
  height: 80px;
  background: radial-gradient(circle at center, #fef3b0, #e5b100);
  border-radius: 50%;
  box-shadow: 0 0 30px 10px rgba(255, 235, 130, 0.5);
  animation: glow 4s ease-in-out infinite;
}

@keyframes glow {
  0%, 100% { box-shadow: 0 0 20px 8px rgba(255, 235, 130, 0.3); }
  50% { box-shadow: 0 0 40px 15px rgba(255, 235, 130, 0.6); }
}

.typed-text {
  white-space: pre-line;
  font-family: 'Georgia', serif;
  line-height: 1.6;
  overflow-y: auto;
}
</style>
