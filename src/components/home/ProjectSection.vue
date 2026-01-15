<script setup>
import { computed } from "vue"
import { useTheme } from "../../composables/useTheme"
import ProjectCard from "../../components/common/ProjectCard.vue"
import { projects } from "../../data/projects"

const { theme } = useTheme()

// preview (home)
const projectsPreview = projects.slice(0, 3)

// theme-based text colors
const titleText = computed(() =>
    theme.value === "light"
      ? "text-[#ec4899] hover:text-black transition"
      : "text-[#d1d5db] hover:text-[#ec4899] transition"
  )

const subText =  computed(() =>
    theme.value === "light"
      ? "text-[#ec4899] hover:text-black transition"
      : "text-[#d1d5db] hover:text-[#ec4899] transition"
  )
</script>

<template>
<section class="py-20 px-6">
  <div class="max-w-6xl mx-auto">

    <!-- HEADER -->
    <div class="flex items-center justify-between mb-10">
      <h2 :class="['text-2xl md:text-3xl font-bold', titleText]">
        <span class="text-pink-400">#</span>projects
      </h2>

      <router-link
        to="/projects"
        :class="['text-sm transition', subText]"
      >
        View all ~~&gt;
      </router-link>
    </div>

    <!-- GRID -->
    <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
      <ProjectCard
        v-for="project in projectsPreview"
        :key="project.id"
        :project="project"
      />
    </div>

  </div>
</section>
</template>
