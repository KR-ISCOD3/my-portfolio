<template>
  <div class="group relative bg-neutral-900 border border-neutral-800 rounded-xl overflow-hidden hover:border-pink-400 transition-all duration-300">

    <div class="relative h-44 bg-neutral-800 flex items-center justify-center overflow-hidden">
      <img v-if="project.image" :src="project.image" :alt="project.title"
           class="w-full h-full object-cover group-hover:scale-105 transition duration-300" />

      <div v-else class="text-gray-500 text-sm tracking-widest uppercase">No Preview</div>

      <div class="absolute inset-0 bg-black/40 opacity-0 group-hover:opacity-100 transition"></div>
    </div>

    <div class="p-5">
      <h3 class="text-lg font-semibold text-white mb-2">{{ project.title }}</h3>

      <p class="text-sm text-gray-400 mb-4 line-clamp-2">{{ project.description }}</p>

      <div class="flex flex-wrap gap-2 mb-4">
        <span v-for="(tech, i) in project.tech" :key="i"
              class="text-xs px-2 py-1 rounded bg-neutral-800 text-pink-400">
          {{ tech }}
        </span>
      </div>

      <a v-if="project.link" :href="project.link" target="_blank" rel="noopener noreferrer"
         class="inline-flex items-center gap-2 text-sm text-pink-400 hover:text-pink-300 transition">
        View Project →
      </a>
    </div>

  </div>
</template>

<script setup>
defineProps({ project: { type: Object, required: true } })
</script>
