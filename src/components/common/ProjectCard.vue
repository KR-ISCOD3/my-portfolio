<script setup>
import { computed } from "vue"
import { useTheme } from "../../composables/useTheme"

defineProps({ project: { type: Object, required: true } })

const { theme } = useTheme()

const cardBg = computed(() =>
  theme.value === "light"
    ? "bg-white border-[#ec4899]/40 hover:shadow-[0_0_30px_rgba(236,72,153,0.25)]"
    : "bg-black border-[#ec4899]/40 hover:shadow-[0_0_40px_rgba(236,72,153,0.35)]"
)

const titleText = computed(() =>
  theme.value === "light" ? "text-black" : "text-white"
)

const bodyText = computed(() =>
  theme.value === "light" ? "text-[#374151]" : "text-[#d1d5db]"
)
</script>

<template>
  <div
    class="group relative rounded-xl overflow-hidden border transition-all duration-300 hover:border-[#ec4899]"
    :class="cardBg"
  >

    <!-- IMAGE -->
    <div class="relative h-44 flex items-center justify-center overflow-hidden">
      <img
        v-if="project.image"
        :src="project.image"
        :alt="project.title"
        class="w-full h-full object-cover group-hover:scale-105 transition duration-300"
      />

      <div v-else class="text-[#ec4899] text-sm tracking-widest uppercase">
        No Preview
      </div>

      <div class="absolute inset-0 bg-[#ec4899]/10 opacity-0 group-hover:opacity-100 transition"></div>
    </div>

    <!-- CONTENT -->
    <div class="p-5">
      <h3 class="text-lg font-semibold mb-2" :class="titleText">
        {{ project.title }}
      </h3>

      <p class="text-sm mb-4 line-clamp-2" :class="bodyText">
        {{ project.description }}
      </p>

      <!-- TECH -->
      <div class="flex flex-wrap gap-2 mb-4">
        <span
          v-for="(tech, i) in project.tech"
          :key="i"
          class="text-xs px-2 py-1 rounded bg-[#ec4899]/10 text-[#ec4899]"
        >
          {{ tech }}
        </span>
      </div>

      <a
        v-if="project.link"
        :href="project.link"
        target="_blank"
        rel="noopener noreferrer"
        class="inline-flex items-center gap-2 text-sm text-[#ec4899] hover:underline transition"
      >
        View Project →
      </a>
    </div>

  </div>
</template>
