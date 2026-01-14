<script setup>
import Header from "../components/common/Header.vue";
import ParticleBackground from "../components/common/ParticleBackground.vue"
</script>

<template>
  <ParticleBackground />

  <div class="relative z-10 min-h-screen text-white p-6">
    <Header />
    <!-- <h1 class="text-4xl font-bold">Hello bro</h1> -->
    <router-view />
  </div>
</template>