<script setup lang="ts">
import { ref } from 'vue'
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue'

// Import Swiper styles
import 'swiper/css'

import 'swiper/css/free-mode'
import 'swiper/css/navigation'
import 'swiper/css/thumbs'

import './style.css'

// import required modules
import { FreeMode, Navigation, Thumbs, A11y } from 'swiper/modules'

const thumbsSwiper = ref()

const setThumbsSwiper = (swiper) => {
  thumbsSwiper.value = swiper
}

const modules = ref([FreeMode, Navigation, Thumbs, A11y])

const getImageURL = (id: number, highRes?: boolean) => {
  const resolution = highRes ? '800/600' : '200/100'

  return `https://picsum.photos/id/${110 + id}/${resolution}`
}
</script>

<template>
  <div>
    <swiper :spaceBetween="10" :navigation="true" :thumbs="{ swiper: thumbsSwiper }" :modules="modules" class="big-gallery">
      <swiper-slide v-for="i in 10">
        <img :src="getImageURL(i, true)" />
      </swiper-slide>
    </swiper>
  </div>
  <swiper @swiper="setThumbsSwiper" :spaceBetween="10" :slidesPerView="4.5" :watchSlidesProgress="true" :grabCursor="true" :modules="modules" class="small-gallery">
    <swiper-slide v-for="i in 10">
      <img :src="getImageURL(i)" />
    </swiper-slide>
  </swiper>
</template>
