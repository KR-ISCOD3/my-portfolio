<script setup>
import { useTheme } from "../../composables/useTheme.js"
const { theme } = useTheme()
</script>

<template>
  <section class="py-24 px-6">
    <div class="max-w-7xl mx-auto">

      <!-- HEADER -->
      <div class="flex items-center gap-4 mb-14">
        <h2 class="text-3xl font-bold" :class="theme === 'dark' ? 'text-white' : 'text-black'">
          <span class="text-pink-400">#</span>skills
        </h2>
        <div class="flex-1 h-px bg-pink-400/40"></div>
      </div>

      <!-- GRID (4 PER ROW) -->
      <div class="grid gap-6 grid-cols-1 sm:grid-cols-2 lg:grid-cols-4">

        <!-- CARD -->
        <div
          class="border p-6"
          :class="theme === 'dark'
            ? 'bg-neutral-900 border-neutral-700 text-gray-300'
            : 'bg-white border-neutral-200 text-gray-700'"
        >
          <h3 class="font-semibold mb-4" :class="theme === 'dark' ? 'text-white' : 'text-black'">
            Languages
          </h3>
          <p>JavaScript</p>
          <p>TypeScript</p>
          <p>Python</p>
        </div>

        <!-- CARD -->
        <div
          class="border p-6"
          :class="theme === 'dark'
            ? 'bg-neutral-900 border-neutral-700 text-gray-300'
            : 'bg-white border-neutral-200 text-gray-700'"
        >
          <h3 class="font-semibold mb-4" :class="theme === 'dark' ? 'text-white' : 'text-black'">
            Frameworks
          </h3>
          <p>React</p>
          <p>Next</p>
          <p>Express</p>
          <p>Flask</p>
          <p>Quart</p>
        </div>

        <!-- CARD -->
        <div
          class="border p-6"
          :class="theme === 'dark'
            ? 'bg-neutral-900 border-neutral-700 text-gray-300'
            : 'bg-white border-neutral-200 text-gray-700'"
        >
          <h3 class="font-semibold mb-4" :class="theme === 'dark' ? 'text-white' : 'text-black'">
            Other
          </h3>
          <p>HTML CSS SASS SCSS</p>
          <p>Less Stylus EJS</p>
          <p>Jinja2 Pug</p>
        </div>

        <!-- CARD -->
        <div
          class="border p-6"
          :class="theme === 'dark'
            ? 'bg-neutral-900 border-neutral-700 text-gray-300'
            : 'bg-white border-neutral-200 text-gray-700'"
        >
          <h3 class="font-semibold mb-4" :class="theme === 'dark' ? 'text-white' : 'text-black'">
            Tools
          </h3>
          <p>Git</p>
          <p>Docker</p>
          <p>Figma</p>
          <p>Postman</p>
        </div>

        <!-- 🔥 5TH CARD (GOES TO NEXT ROW) -->
        <div
          class="border p-6"
          :class="theme === 'dark'
            ? 'bg-neutral-900 border-neutral-700 text-gray-300'
            : 'bg-white border-neutral-200 text-gray-700'"
        >
          <h3 class="font-semibold mb-4" :class="theme === 'dark' ? 'text-white' : 'text-black'">
            Databases
          </h3>
          <p>SQLite</p>
          <p>PostgreSQL</p>
          <p>MongoDB</p>
        </div>

      </div>
    </div>
  </section>
</template>
