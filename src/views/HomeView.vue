<script setup>
import { ref } from "vue";
const selectedColor = ref(0);

const carModels = [
  {
    title: "MINI Cooper S Countryman",
    price: "RM 250,388.00",
    monthly: "RM 2,220.00",
    colors: [
      {
        image: "/images/1-chile-red.png",
        thumbnail: "/images/1-chile-red.webp",
        name: "Chile Red"
      },
      {
        image: "/images/2-sage-green.png",
        thumbnail: "/images/2-sage-green.webp",
        name: "Sage Green"
      },
      {
        image: "/images/3-british-green.png",
        thumbnail: "/images/3-british-green.webp",
        name: "British Green"
      },
      {
        image: "/images/4-nanuq-white.png",
        thumbnail: "/images/4-nanuq-white.webp",
        name: "Nanuq White"
      },
      {
        image: "/images/5-island-blue.png",
        thumbnail: "/images/5-island-blue.webp",
        name: "Island Blue"
      }
    ]
  }
];


const selectColor = (color) => {
  console.log(color);
  selectedColor.value = color;
};
</script>

<template>
  <div class="overview-view mobile" v-for="car in carModels">
    <div class="w-100 mb-10">
      <v-window v-model="selectedColor">
        <v-window-item
          v-for="(cl, index) in car.colors"
          :key="index"
          class="text-center"
          eager>
          <v-img :src="cl.image" aspect-ratio="16/9" class="mb-5" eager></v-img>
          <h4 class="bold" v-html="cl.name"></h4>
        </v-window-item>
      </v-window>
    </div>
    <div class="w-100">
      <h2 class="bold mb-2" v-html="car.title"></h2>
      <p>Retail Price</p>
      <h3 class="bold mb-2" v-html="car.price"></h3>
      <p>Monthly Installment</p>
      <h3 class="bold" v-html="car.monthly"></h3>

      <v-slide-group class="mb-10">
        <v-slide-group-item
          v-model="selectedColor"
          v-for="(cl, index) in car.colors"
          :key="index"
          v-slot="CurColor">
          <v-sheet
            class="color-tab rounded-circle elevation-3"
            :style="{ backgroundImage: cl.thumbnail }"
            @click="selectColor(index)"
            active-class="selected-circle"
            :class="CurColor">
            <v-img :src="cl.thumbnail" cover></v-img>
          </v-sheet>
        </v-slide-group-item>
      </v-slide-group>
      <v-btn variant="outlined" class="mb-5" color="indigo" block>
        Add To Cart
      </v-btn>
      <v-btn variant="elevated" color="indigo" block>Buy Now</v-btn>
    </div>
  </div>
</template>

<style>
h1 + div {
  width: 100%;
}

.overview-view {
  display: flex;
  margin-top: 90px !important;

  & * {
    transition: all 0.5s ease;
  }

  .v-window-item {
    transition: none;
  }

  .bold{
    font-weight: 700;
  }

  .color-tab {
    border: solid 2px #fff;
    height: 50px;
    width: 50px;
    overflow: hidden;
  }

  .v-slide-group__content {
    min-height: 65px;
    gap: 22px;
    justify-content: center;
    margin-top: 20px;
    align-items: center;

    .isSelected {
      border: solid 2px var(--vt-c-blue);
      height: 55px;
      width: 55px;
    }
  }
}

@media (max-width: 768px) {
  .mobile{
    display: block;
  }
}
</style>
