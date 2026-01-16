<script setup>
import { useTheme } from "../../composables/useTheme.js"
import SkillCard from "../common/SkillCard.vue"

const { theme } = useTheme()

const skills = [
  {
    title: "Languages",
    items: ["JavaScript", "TypeScript", "Python"]
  },
  {
    title: "Frameworks",
    items: ["React", "Next", "Express", "Flask", "Quart"]
  },
  {
    title: "Other",
    items: ["HTML CSS SASS SCSS", "Less Stylus EJS", "Jinja2 Pug"]
  },
  {
    title: "Databases",
    items: ["SQLite", "PostgreSQL", "MongoDB"]
  },
  {
    title: "Tools",
    items: ["Git", "Docker", "Figma", "Postman"]
  }
]
</script>

<template>
  <section class="py-10 px-4 md:px-6">
    <div class="max-w-6xl mx-auto">
      <div class="flex items-center justify-start gap-4 mb-14">
        <h2 class="text-3xl font-bold" :class="theme==='dark'?'text-white':'text-black'"><span class="text-pink-400">#</span>skills</h2>
      </div>

      <div class="columns-1 sm:columns-2 lg:columns-4 gap-6 masonry-start">
        <SkillCard v-for="(skill,i) in skills" :key="i" :title="skill.title" :items="skill.items" />
      </div>
    </div>
  </section>
</template>
