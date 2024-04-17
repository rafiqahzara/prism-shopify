<script setup lang="ts">
import TheWelcome from '../components/TheWelcome.vue'

const carModels = [
  {
    img: "/images/1-chile-red.png",
    thumbnail: "/images/1-chile-red.webp",
    name: "Chile Red"
  },

  {
    img: "/images/2-sage-green.png",
    thumbnail: "/images/2-sage-green.webp",
    name: "Sage Green"
  },
]
</script>

<template>
  <v-carousel>
    <v-carousel-item
      src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
      cover></v-carousel-item>

    <v-carousel-item
      src="https://cdn.vuetifyjs.com/images/cards/hotel.jpg"
      cover></v-carousel-item>

    <v-carousel-item
      src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
      cover></v-carousel-item>
  </v-carousel>
</template>
