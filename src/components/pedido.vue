<template>
  <v-app>
    <!-- Fundo da praia -->
    <div class="beach-background">
      <div class="sun"></div>


      <!-- Ondas animadas -->
      <div class="ocean">
        <div class="wave wave1"></div>
        <div class="wave wave2"></div>
        <div class="wave wave3"></div>
      </div>

      <!-- Faixa de areia -->
      <div class="sand"></div>
    </div>

    <!-- Card central com mensagem -->
    <v-main class="d-flex align-center justify-center flex-column" style="gap: 20px;">
      <div class="marshmallow" />

      <v-card class="beach-card pa-6 text-center overflow-y-auto" max-width="90%" width="500">
        <div class="shell shell-left">🐚</div>
        <div class="shell shell-right">🐚</div>

        <v-card-text class="text-subtitle-1 message-text fade-in-delay">
          Depois de tantas marés e correntes...<br />
          Aceita ser meu <b>Atlas</b> e navegar comigo?
        </v-card-text>

        <v-card-actions class="justify-center mt-4 fade-in-delay">
          <v-btn color="deep-purple accent-4" @click="showSecondCard = true" class="accept-btn" depressed>
            Sim
          </v-btn>
        </v-card-actions>
      </v-card>

      <v-card class="beach-card pa-6 text-center" max-width="90%" width="500" v-if="showSecondCard">
        <v-btn icon class="back-button" style="position: absolute; left: 10px; top: 10px;"
               @click="$router.push({ name: 'Home' })">
          <v-icon>mdi-arrow-left</v-icon>
        </v-btn>
        <img src="/public/imagens/personagens_praia.png" alt="Personagem dançando"
             style="max-width: 200px; width: 100%;" class="dancing-image" />
        <v-card-text class="text-subtitle-1 message-text fade-in-delay">
          Pode parar de nadar...<br />
          Você chegou à Costa. 💙
        </v-card-text>
      </v-card>
    </v-main>

    <!-- Música ambiente -->
    <audio autoplay loop style="display: none">
      <source src="/public/musicas/crepusculo.mp3" type="audio/mp3" />
    </audio>

    <!-- Sons do mar e gaivotas -->
    <audio autoplay loop style="display: none">
      <source src="/public/musicas/mar.mp3" type="audio/mp3" />
    </audio>
  </v-app>
</template>

<script setup>
import { ref } from 'vue'
const showSecondCard = ref(false)
</script>

<style scoped>
/* Fundo céu */
.beach-background {
  position: fixed;
  inset: 0;
  background: linear-gradient(to top, #87ceeb 0%, #b2e0f7 100%);
  overflow: hidden;
  z-index: 0;
}

/* Sol */
.sun {
  position: absolute;
  top: 40px;
  left: 40px;
  width: 100px;
  height: 100px;
  background: radial-gradient(circle, #fff59d, #fdd835);
  border-radius: 50%;
  box-shadow: 0 0 80px #ffeb3b;
  animation: sunPulse 6s ease-in-out infinite;
}

@keyframes sunPulse {
  0%, 100% { transform: scale(1); opacity: 1; }
  50% { transform: scale(1.05); opacity: 0.9; }
}

/* Estrela cadente */
.shooting-star {
  position: absolute;
  top: 20%;
  left: 10%;
  width: 2px;
  height: 2px;
  background: white;
  animation: shoot 6s ease-in-out infinite;
  z-index: 2;
}

@keyframes shoot {
  0% { transform: translate(0, 0); opacity: 1; }
  100% { transform: translate(300px, 100px); opacity: 0; }
}

/* Oceano */
.ocean {
  position: absolute;
  bottom: 100px;
  width: 100%;
  height: 200px;
  background: linear-gradient(to top, #00bcd4, #4dd0e1);
  z-index: 1;
}

.wave {
  position: absolute;
  bottom: 0;
  width: 200%;
  height: 100%;
  background: rgba(255, 255, 255, 0.3);
  border-radius: 45% 55% 50% 50%;
  animation: waveAnimation 10s linear infinite;
  opacity: 0.3;
}

.wave1 { animation-delay: 0s; height: 40px; }
.wave2 { animation-delay: 3s; bottom: 10px; height: 30px; opacity: 0.25; }
.wave3 { animation-delay: 6s; bottom: 20px; height: 20px; opacity: 0.2; }

@keyframes waveAnimation {
  0% { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}

/* Areia */
.sand {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 100px;
  background: linear-gradient(to top, #fbeec2, #f3d89c);
  z-index: 2;
}

/* Card */
.beach-card {
  z-index: 10;
  background: linear-gradient(145deg, #ffffff, #f0f8ff);
  backdrop-filter: blur(12px);
  border-radius: 24px;
  box-shadow: 0 12px 32px rgba(0, 0, 0, 0.2);
  border: 2px solid rgba(255, 255, 255, 0.4);
  position: relative;
  overflow: hidden;
  animation: fadeIn 1.2s ease-in-out both;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.beach-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 16px 40px rgba(0, 0, 0, 0.25);
}

.message-text {
  color: #263238;
  font-family: 'Segoe UI', sans-serif;
  margin-top: 12px;
  line-height: 1.6;
}

.accept-btn {
  border-radius: 20px;
  padding: 0 24px;
  color: white;
  font-weight: bold;
  font-size: 16px;
  transition: transform 0.3s;
}

.accept-btn:hover {
  transform: scale(1.05);
}

.shell {
  position: absolute;
  font-size: 28px;
  opacity: 0.5;
}

.shell-left { bottom: 16px; left: 16px; }
.shell-right { top: 16px; right: 16px; }

@keyframes fadeIn {
  0% { opacity: 0; transform: translateY(20px); }
  100% { opacity: 1; transform: translateY(0); }
}

.fade-in-delay {
  animation: fadeIn 1.5s ease forwards;
}

.dancing-image {
  animation: dance 2s infinite alternate ease-in-out;
  filter: drop-shadow(0 0 10px white);
}

@keyframes dance {
  0%   { transform: rotate(-5deg) translateY(0); }
  50%  { transform: rotate(5deg) translateY(-10px); }
  100% { transform: rotate(-5deg) translateY(0); }
}

/* Responsivo */
@media (max-width: 600px) {
  .sun {
    width: 80px;
    height: 80px;
    top: 20px;
    left: 20px;
  }

  .ocean {
    bottom: 60px;
    height: 150px;
  }

  .sand {
    height: 80px;
  }
}
</style>
