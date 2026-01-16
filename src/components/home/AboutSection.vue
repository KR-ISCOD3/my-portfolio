<script setup>
import { useTheme } from "../../composables/useTheme.js"

const { theme } = useTheme()

// 🔥 About data (backend-ready)
const about = {
  title: "about",
  paragraphs: [
    "I’m a self-taught front-end developer based in Warsaw, Poland. I can develop responsive websites from scratch and raise them into modern user-friendly web experiences.",
    "Transforming my creativity and knowledge into websites has been my passion for over two years. I have been helping various clients establish their presence online. I always strive to learn about the newest technologies and frameworks."
  ],
  buttonText: "View all →",
  image: "image/i4.png"
}
</script>

<template>
  <section class="py-20 px-4 md:px-6">
    <div class="max-w-6xl mx-auto grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">

      <!-- LEFT : TEXT -->
      <div>
        <!-- TITLE -->
        <div class="flex items-center gap-4 mb-10">
          <h2 class="text-3xl font-bold" :class="theme==='dark'?'text-white':'text-black'">
            <span class="text-pink-400">#</span>{{ about.title }}
          </h2>
          <div class="flex-1 h-px bg-pink-400/40"></div>
        </div>

        <!-- PARAGRAPHS -->
        <p
          v-for="(text, i) in about.paragraphs"
          :key="i"
          class="leading-relaxed mb-6"
          :class="theme==='dark'?'text-gray-300':'text-gray-700'"
        >
          {{ text }}
        </p>

        <!-- BUTTON -->
        <a
          href="#"
          class="bg-pink-500 hover:bg-pink-600 text-white px-6 py-2 rounded-md transition"
          :class="theme==='dark'
            ? 'border-pink-400 text-white'
            : 'border-pink-500 text-black'"
        >
          {{ about.buttonText }}
        </a>
      </div>

      <!-- RIGHT : IMAGE -->
      <div class="relative">
        <img
          :src="about.image"
          alt="About image"
          class="w-full max-w-md ml-auto object-cover"
        />

        <span class="absolute bottom-0 left-0 w-full h-px bg-pink-400/40 mt-3"></span>
      </div>

    </div>
  </section>
</template>
