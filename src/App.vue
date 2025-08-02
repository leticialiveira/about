<template>
  <v-app>
    <!-- Fundo animado fixo -->
    <div class="background-stars">
      <div
        v-for="(star, index) in stars"
        :key="index"
        class="star"
        :style="{
          top: `${star.top}%`,
          left: `${star.left}%`,
          animationDuration: `${star.duration}s`
        }"
      />
    </div>

    <!-- Conteúdo principal -->
    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const stars = ref([])

onMounted(() => {
  stars.value = Array.from({ length: 100 }, () => ({
    top: Math.random() * 100,
    left: Math.random() * 100,
    duration: 1 + Math.random() * 2,
  }))
})
</script>

<style scoped>
.background-stars {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(ellipse at bottom, #0b1d3a 0%, #050d1a 100%);
  z-index: 0;
  overflow: hidden;
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
  0%, 100% {
    opacity: 0.2;
  }
  50% {
    opacity: 1;
  }
}

/* Garante que o conteúdo fique acima do fundo */
.v-main {
  position: relative;
  z-index: 1;
}
</style>
