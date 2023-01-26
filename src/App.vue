<script setup lang="ts">
import { ref } from "vue";
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from "swiper/vue";

// Import Swiper styles
import "swiper/css";

import "swiper/css/free-mode";
import "swiper/css/navigation";
import "swiper/css/thumbs";

import "./style.css";

// import required modules
import { FreeMode, Navigation, Thumbs } from "swiper";

const thumbsSwiper = ref();

const setThumbsSwiper = (swiper) => {
  thumbsSwiper.value = swiper;
};

const modules = ref([FreeMode, Navigation, Thumbs]);
</script>

<template>
  <swiper
    :style="{
      '--swiper-navigation-color': '#fff',
      '--swiper-pagination-color': '#fff',
    }"
    :spaceBetween="10"
    :navigation="true"
    :thumbs="{ swiper: thumbsSwiper }"
    :modules="modules"
    class="mySwiper2"
  >
    <swiper-slide v-for="i in 10">
      <img :src="`https://picsum.photos/id/${110 + i}/800/600`" />
    </swiper-slide>
  </swiper>
  <swiper
    @swiper="setThumbsSwiper"
    :spaceBetween="10"
    :slidesPerView="4"
    :freeMode="true"
    :watchSlidesProgress="true"
    :grabCursor="true"
    :modules="modules"
    class="mySwiper"
  >
    <swiper-slide v-for="i in 10">
      <img :src="`https://picsum.photos/id/${110 + i}/200/100`" />
    </swiper-slide>
  </swiper>
</template>
