<script setup>
import { useTheme } from "../../composables/useTheme.js"

defineProps({
  title: {
    type: String,
    required: true
  },
  items: {
    type: Array,
    required: true
  }
})

const { theme } = useTheme()
</script>

<template>
  <div class="mb-6 break-inside-avoid border p-6" :class="theme==='dark'?'bg-neutral-900 border-neutral-700 text-gray-300':'bg-white border-neutral-200 text-gray-700'">
    <h3 class="font-semibold mb-4" :class="theme==='dark'?'text-white':'text-black'">{{ title }}</h3>
    <ul class="space-y-1">
      <li v-for="(item,i) in items" :key="i">{{ item }}</li>
    </ul>
  </div>
</template>
