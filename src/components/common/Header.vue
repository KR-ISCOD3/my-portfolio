<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue"

const openLang = ref(false)
const openMenu = ref(false)

const closeAll = (e) => {
  if (!e.target.closest(".lang-menu")) openLang.value = false
}

onMounted(() => document.addEventListener("click", closeAll))
onBeforeUnmount(() => document.removeEventListener("click", closeAll))
</script>

<template>
  <header class="w-full py-3 relative">
    <!-- DESKTOP NAV -->
    <nav class="hidden md:flex justify-center items-center gap-9 text-md font-medium">
      <router-link to="/" exact-active-class="text-pink-400 uppercase font-bold" class="text-gray-300 hover:text-pink-400 transition hover:underline"><span class="text-pink-400">#</span>home</router-link>
      <router-link to="/projects" active-class="text-pink-400 uppercase font-bold" class="text-gray-300 hover:text-pink-400 transition hover:underline"><span class="text-pink-400">#</span>projects</router-link>
      <router-link to="/contact" active-class="text-pink-400 uppercase font-bold" class="text-gray-300 hover:text-pink-400 transition hover:underline"><span class="text-pink-400">#</span>about-me</router-link>
      
      <router-link to="#" active-class="text-pink-400 uppercase font-bold" class="text-gray-300 hover:text-pink-400 transition hover:underline"><span class="text-pink-400">#</span>tool</router-link>
      <router-link to="#" active-class="text-pink-400 uppercase font-bold" class="text-gray-300 hover:text-pink-400 transition hover:underline"><span class="text-pink-400">#</span>other-skills</router-link>

      <!-- Language -->
      <div class="relative lang-menu">
        <button @click.stop="openLang = !openLang" class="text-gray-300 hover:text-pink-400 transition hover:underline">EN ▾</button>
        <div v-show="openLang" class="absolute left-1/2 -translate-x-1/2 mt-2 bg-neutral-900 border border-neutral-700 rounded-md text-xs z-50 min-w-20">
          <button class="block px-4 py-2 hover:bg-neutral-800 w-full text-left">EN</button>
          <button class="block px-4 py-2 hover:bg-neutral-800 w-full text-left">KH</button>
        </div>
      </div>
    </nav>

    <!-- MOBILE HEADER -->
    <div class="flex md:hidden justify-between items-center px-4">
      <span class="text-pink-400 font-semibold">#portfolio</span>

      <button @click="openMenu = true" class="text-gray-300">
        ☰
      </button>
    </div>

    <!-- MOBILE SIDEBAR -->
    <div v-show="openMenu" class="fixed inset-0 z-50 flex">
      <!-- overlay -->
      <div class="flex-1 bg-black/60" @click="openMenu = false"></div>

      <!-- drawer -->
      <div class="w-64 bg-neutral-900 p-6 flex flex-col gap-6 text-sm">
        <button class="self-end text-gray-400" @click="openMenu = false">✕</button>

        <router-link @click="openMenu = false" to="/" class="text-gray-300 hover:text-pink-400"><span class="text-pink-400">#</span>home</router-link>
        <router-link @click="openMenu = false" to="/projects" class="text-gray-300 hover:text-pink-400"><span class="text-pink-400">#</span>projects</router-link>
        <router-link @click="openMenu = false" to="/contact" class="text-gray-300 hover:text-pink-400"><span class="text-pink-400">#</span>about-me</router-link>

        <div class="border-t border-neutral-700 pt-4">
          <p class="text-xs text-gray-400 mb-2">Language</p>
          <button class="block text-left text-gray-300 hover:text-pink-400">EN</button>
          <button class="block text-left text-gray-300 hover:text-pink-400">KH</button>
        </div>
      </div>
    </div>
  </header>
</template>
