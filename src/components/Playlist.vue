<template>
  <v-container class="custom-starry-bg overflow-y-auto fill-height" max-width="900" style="max-height: 100vh;"> 
     <v-btn icon class="back-button" @click="$router.push({ name: 'Home' })">
      <v-icon>mdi-arrow-left</v-icon>
    </v-btn>
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
   
    <v-card class="pa-6 d-flex flex-column align-center" style="width: 100%; background-color: #162b4c; color: white;">
      <img
        :src="currentSong.image"
        alt="Personagem dançando"
        style="max-width: 200px; width: 100%;"
        :class="img_show ? 'dancing-image' : ''"
      />
      <v-card-title class="text-h6 text-center">
        🎵 {{ currentSong.title }}
      </v-card-title>

      <audio
        ref="audioPlayer"
        :src="currentSong.src"
        @ended="playNext"
        @loadedmetadata="setDuration"
      ></audio>

      <v-card-text class="d-flex justify-center align-center mt-4">
        <v-btn icon @click="playPrevious">
          <v-icon>mdi-skip-previous</v-icon>
        </v-btn>

        <v-btn icon @click="togglePlay">
          <v-icon>{{ isPlaying ? 'mdi-pause' : 'mdi-play' }}</v-icon>
        </v-btn>

        <v-btn icon @click="playNext">
          <v-icon>mdi-skip-next</v-icon>
        </v-btn>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue'

const playlist = [
  {
    image: '/public/imagens/personagens_noite.png',
    title: 'Ter o coração no chão',
    src: '/public/musicas/coracao_chao.mp3'
  },
  {
    image: '/public/imagens/personagens_praia.png',
    title: 'Pra Sonhar',
    src: '/public/musicas/pra_sonhar.mp3'
  },
  {
    image: '/public/imagens/personagens_noite.png',
    title: 'Clair de Lune',
    src: '/public/musicas/Clair_De_Lune.mp3'
  },
  {
    image: '/public/imagens/personagens_praia.png',
    title: 'Cacos',
    src: '/public/musicas/cacos.mp3'
  },
  {
    image: '/public/imagens/personagens_noite.png',
    title: 'Prisão sem Grade',
    src: '/public/musicas/prisao_sem_grade.mp3'
  },
  {
    image: '/public/imagens/personagens_praia.png',
    title: 'Só hoje',
    src: '/public/musicas/so_hoje.mp3'
  },
  {
    image: '/public/imagens/personagens_noite.png',
    title: 'Último Romance',
    src: '/public/musicas/ultimo_romance.mp3'
  },
  {
    image: '/public/imagens/personagens_praia.png',
    title: 'Olhos Castanhos',
    src: '/public/musicas/olhos_castanhos.mp3'
  },
   {
    image: '/public/imagens/personagens_noite.png',
    title: 'Those Eyes',
    src: '/public/musicas/those_eyes.mp3'
  },
  {
    image: '/public/imagens/personagens_praia.png',
    title: 'Nessas horas',
    src: '/public/musicas/horas.mp3'
  },
   {
    image: '/public/imagens/personagens_noite.png',
    title: 'Olha',
    src: '/public/musicas/olha.mp3'
  },
]

const audioPlayer = ref(null)
const currentIndex = ref(0)
const isPlaying = ref(false)
let img_show = ref(true)
const stars = ref([])

const currentSong = computed(() => playlist[currentIndex.value])

function togglePlay() {
  img_show.value = false

  if (!audioPlayer.value) return
  if (isPlaying.value) {
    img_show.value = false
    audioPlayer.value.pause()
  } else {
    img_show.value = true
    audioPlayer.value.play()
  }
  isPlaying.value = !isPlaying.value
}

function playNext() {
  currentIndex.value = (currentIndex.value + 1) % playlist.length
  playCurrent()
}

function playPrevious() {
  currentIndex.value = (currentIndex.value - 1 + playlist.length) % playlist.length
  playCurrent()
}

function playCurrent() {
  if (!audioPlayer.value) return
  isPlaying.value = false
  audioPlayer.value.pause()
  audioPlayer.value.load()
  audioPlayer.value.play()
  isPlaying.value = true
}

function setDuration() {
  if (!audioPlayer.value || !isPlaying.value) return
  audioPlayer.value.play()
}

onMounted(() => {
  // Autoplay a primeira
  setTimeout(() => playCurrent(), 500)

  // Estrelas
  const totalStars = 150
  stars.value = Array.from({ length: totalStars }, () => ({
    top: Math.random() * 100,
    left: Math.random() * 100,
    duration: 1 + Math.random() * 2
  }))
})
</script>

<style scoped>
.v-icon {
  color: white;
  font-size: 32px;
}

.dancing-image {
  animation: dance 0.9s infinite alternate ease-in-out;
  filter: drop-shadow(0 0 10px white);
}

@keyframes dance {
  0% {
    transform: rotate(-5deg) translateY(0);
  }
  50% {
    transform: rotate(5deg) translateY(-10px);
  }
  100% {
    transform: rotate(-5deg) translateY(0);
  }
}

.custom-starry-bg {
  background: radial-gradient(ellipse at bottom, #0b1d3a 0%, #050d1a 100%);
  overflow: hidden;
  position: relative;
  border-radius: 12px;
}

/* Estrelas fixas */
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

/* Lua */
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

.v-expansion-panel {
  background-color: #0b1d3a;
}
</style>

