<template>
  <v-container class="d-flex flex-column align-center justify-center py-8">
    <span class="text-h6 mb-6">✨ E vamos de spoiler dos próximos capítulos ✨</span>

    <v-row dense align="center" justify="center" class="image-grid">
      <v-col
        v-for="(image, index) in images"
        :key="index"
        cols="12"
        sm="6"
        md="4"
        lg="3"
        class="d-flex justify-center"
      >
        <v-card
          class="spoiler-card d-flex flex-column align-center pa-4"
          elevation="10"
        >
          <img
            :src="image.image"
            :alt="image.title"
            class="spoiler-image mb-2"
          />
          <div class="spoiler-title">{{ image.title }}</div>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
const images = [
  { image: '/public/imagens/personagens_aviao.png', title: '✈️' },
  { image: '/public/imagens/personagens_namoro.png', title: '💗💙' },
  { image: '/public/imagens/personagens_morar.png', title: '🏠' },
  { image: '/public/imagens/personagens_casamento.png', title: '💍' },
  { image: '/public/imagens/personagens_gravidez.png', title: '🤰' },
  { image: '/public/imagens/personagens_familia.png', title: '👨‍👩‍👧' },
  { image: '/public/imagens/personagens_velhinhos.png', title: '👴👵' }
];
</script>

<style scoped>
.image-grid {
  max-width: 1200px;
  margin: auto;
}

.spoiler-card {
  width: 100%;
  max-width: 250px;
  background-color: #0b1d3a;
  border-radius: 16px;
  text-align: center;
  transition: transform 0.3s ease;
}

.spoiler-card:hover {
  transform: translateY(-5px);
}

.spoiler-image {
  width: 100%;
  max-width: 200px;
  border-radius: 12px;
  filter: drop-shadow(0 0 4px rgba(255, 255, 255, 0.2));
}

.spoiler-title {
  color: white;
  font-weight: 500;
  font-size: 16px;
  margin-top: 8px;
  font-family: 'Segoe UI', sans-serif;
}

/* Responsivo para tela pequena */
@media (max-width: 600px) {
  .spoiler-image {
    max-width: 150px;
  }

  .spoiler-title {
    font-size: 14px;
  }
}
</style>
