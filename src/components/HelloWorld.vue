<template>
  <v-container class="custom-starry-bg fill-height" max-width="900" style="max-height: 100vh;">
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

    <div class="moon"></div>

    
    <div class="fill-height d-flex align-center justify-center flex-column" style="width: 100%;">
      <h1 style="font-family: Brush Script MT, Brush Script Std, cursive; font-weight: 100; text-align: center; margin: 20px 0;">About Us</h1>
      <v-card class="d-flex flex-column pa-4" style="width: 90%; max-width: 600px; background-color:#0b1d3a;">
        <v-card-title class="text-h5" style="color:aliceblue">
          Querido Rick,
        </v-card-title>
        <v-card-text class="typed-text text-h6" style="color:aliceblue; min-height: 200px;">
          {{ typedText }}
        </v-card-text>
        <v-card-actions class="d-flex justify-center">
          <v-btn icon @click="$router.push({ name: 'About Us' })">
            <v-icon>mdi mdi-book-open-variant</v-icon>
          </v-btn>
          <v-btn icon @click="$router.push({ name: 'Pedido' })">
            <v-icon>mdi-heart</v-icon>
          </v-btn>
          <v-btn icon @click="$router.push({ name: 'Musicas' })">
            <v-icon>mdi mdi-music</v-icon>
          </v-btn>
        </v-card-actions>
      </v-card>
    </div>

    
  </v-container>
</template>

<script setup>
import { ref, onMounted } from 'vue'


const stars = ref([])
const fullText = `Quando Letty e Henrique foram à exposição de Van Gogh, eles não conseguiram ver a tão aguardada Noite Estrelada. Mas Letty deu um jeitinho de criar essa mesma magia só para você!
Você merece alguém que não precise voltar no tempo para organizar as coisas. Você merece alguém que faça você voltar no tempo só para reviver tudo da mesma forma. Espero que Letty 
te ajude a conquistar essa forma de ver a vida e que você entenda, Rick, que não precisa sofrer para se encaixar em um lugar tão apertado. Então vou te apresentar o inicio desse céu de infinitas estrelas por tópicos...`

const typedText = ref('')
onMounted(() => {
  const totalStars = 150
  stars.value = Array.from({ length: totalStars }, () => ({
    top: Math.random() * 100,
    left: Math.random() * 100,
    duration: 1 + Math.random() * 2
  }))

  let i = 0
  const interval = setInterval(() => {
    if (i < fullText.length) {
      typedText.value += fullText[i++]
    } else {
      clearInterval(interval)
    }
  }, 25)
})
</script>

<style scoped>
.custom-starry-bg {
  background: radial-gradient(ellipse at bottom, #0b1d3a 0%, #050d1a 100%);
  overflow: hidden;
  position: relative;
  border-radius: 12px;
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

