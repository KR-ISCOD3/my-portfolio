<template>
  <section class="py-20 px-6">
    <div class="max-w-6xl mx-auto">

      <!-- HEADER -->
      <div class="flex items-center justify-between mb-10">
        <h2 class="text-2xl md:text-3xl font-bold text-white">
          <span class="text-pink-400">#</span>projects ------------
        </h2>

        <router-link
          to="/projects"
          class="text-sm text-gray-300 hover:text-pink-400 transition"
        >
          View all ~~&gt;
        </router-link>
      </div>

      <!-- GRID -->
      <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
        <!-- <ProjectCard
          v-for="project in projects"
          :key="project.id"
          :project="project"
        /> -->
      </div>

    </div>
  </section>
</template>

<script setup>
// import ProjectCard from "@/components/common/ProjectCard.vue"
// import { projects } from "@/data/projects"

// show only first 3 on home
// const projectsPreview = projects.slice(0, 3)
</script>
