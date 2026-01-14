<template>
  <section class="relative min-h-[calc(100vh-80px)] flex items-center justify-center px-6">
    <div class="max-w-3xl w-full text-center">

      <!-- AVATAR -->
      <div class="flex justify-center mb-8">
        <Swiper
          effect="cards"
          grabCursor
          :modules="modules"
          :autoplay="{ delay: 2500, disableOnInteraction: false }"
          class="avatar-swiper"
        >
          <SwiperSlide v-for="(img, i) in images" :key="i">
            <img :src="img" alt="avatar" class="avatar-img" />
          </SwiperSlide>
        </Swiper>
      </div>

      <!-- TEXT -->
      <p class="text-pink-400 text-sm tracking-widest mb-4">HELLO, I AM</p>

      <h1 class="text-4xl md:text-6xl font-extrabold mb-4">
        <span class="text-white">Rak</span>
        <span class="text-pink-400"> Smey</span>
      </h1>

      <p class="text-gray-300 mb-8 mx-auto max-w-xl">
        A passionate <span class="text-pink-400">Web Developer</span>
        building modern, fast and beautiful web experiences.
      </p>

      <div class="flex justify-center gap-4 flex-wrap">
        <router-link
          to="/projects"
          class="px-6 py-3 bg-pink-500 hover:bg-pink-600 text-white rounded-md transition"
        >
          View Projects
        </router-link>

        <router-link
          to="/contact"
          class="px-6 py-3 border border-pink-400 text-pink-400 hover:bg-pink-400 hover:text-black rounded-md transition"
        >
          Contact Me
        </router-link>
      </div>

    </div>
  </section>
</template>

<script setup>
import { Swiper, SwiperSlide } from "swiper/vue"
import { EffectCards, Autoplay } from "swiper/modules"

import "swiper/css"
import "swiper/css/effect-cards"

const modules = [EffectCards, Autoplay]

const images = [
  "/image/i1.png",
  "/image/i2.png",
  "/image/i3.png",
]
</script>

<style scoped>
.avatar-swiper {
  width: 180px;
  height: 220px;
}

.avatar-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 16px;
  border: 2px solid rgb(236 72 153);
  box-shadow: 0 0 40px rgba(236, 72, 153, 0.6);
}

.swiper {
  animation: float 6s ease-in-out infinite;
}

@keyframes float {
  0% { transform: translateY(0); }
  50% { transform: translateY(-14px); }
  100% { transform: translateY(0); }
}
</style>
