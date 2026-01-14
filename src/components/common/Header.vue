<script setup>
  import { ref, onMounted, onBeforeUnmount, computed } from "vue"
  import { useTheme } from "../../composables/useTheme.js"

  const openLang = ref(false)
  const openMenu = ref(false)
  const { theme, toggleTheme } = useTheme()

  const closeLang = e => { if (!e.target.closest(".lang-menu")) openLang.value = false }
  onMounted(() => document.addEventListener("click", closeLang))
  onBeforeUnmount(() => document.removeEventListener("click", closeLang))

  /* ✅ THE ONLY NEW THING */
  const navText = computed(() =>
    theme.value === "light"
      ? "text-[#ec4899] hover:text-[#d1d5db] transition"
      : "text-[#d1d5db] hover:text-[#ec4899] transition"
  )
</script>

<template>
  <header class="w-full py-3 relative">

      <!-- DESKTOP -->
      <nav class="hidden md:flex justify-center items-center gap-9 text-md font-medium">

          <router-link to="/" exact-active-class="text-[#ec4899] uppercase font-bold" :class="navText">
            <span class="text-[#ec4899]">#</span>home
          </router-link>

          <router-link to="/projects" active-class="text-[#ec4899] uppercase font-bold" :class="navText">
            <span class="text-[#ec4899]">#</span>projects
          </router-link>

          <router-link to="/contact" active-class="text-[#ec4899] uppercase font-bold" :class="navText">
            <span class="text-[#ec4899]">#</span>about-me
          </router-link>

          <router-link to="#" :class="navText">
            <span class="text-[#ec4899]">#</span>tool
          </router-link>

          <router-link to="#" :class="navText">
            <span class="text-[#ec4899]">#</span>other-skills
          </router-link>

          <!-- LANGUAGE -->
          <div class="relative lang-menu">
          <button @click.stop="openLang = !openLang" :class="navText">EN ▾</button>

          <div v-show="openLang"
              class="absolute left-1/2 -translate-x-1/2 mt-2
                      bg-black border border-[#ec4899]
                      rounded-md text-xs z-50 min-w-20">

          <button class="block px-4 py-2 hover:bg-[#ec4899] hover:text-black w-full text-left">EN</button>
          <button class="block px-4 py-2 hover:bg-[#ec4899] hover:text-black w-full text-left">KH</button>

          </div>
          </div>

          <!-- THEME -->
          <button @click="toggleTheme" :class="navText">
          {{ theme === "dark" ? "☀️" : "🌙" }}
          </button>

      </nav>

      <!-- MOBILE TOP -->
      <div class="flex md:hidden justify-between items-center px-4">
        <span class="text-[#ec4899] font-semibold">#portfolio</span>
        <div class="flex items-center gap-4">
          <button @click="toggleTheme" class="text-[#ec4899]">{{ theme === "dark" ? "☀️" : "🌙" }}</button>
          <button @click="openMenu = true" class="text-[#ec4899]">☰</button>
        </div>
      </div>

      <!-- MOBILE SIDEBAR -->
      <div v-show="openMenu" class="fixed inset-0 z-50 flex">
        <div class="flex-1 bg-black/60" @click="openMenu = false"></div>

        <div class="w-64 bg-black p-6 flex flex-col gap-6 text-sm">

          <button class="self-end text-[#d1d5db]" @click="openMenu = false">✕</button>

          <router-link @click="openMenu=false" to="/" :class="navText">
            <span class="text-[#ec4899]">#</span>home
          </router-link>

          <router-link @click="openMenu=false" to="/projects" :class="navText">
            <span class="text-[#ec4899]">#</span>projects
          </router-link>

          <router-link @click="openMenu=false" to="/contact" :class="navText">
            <span class="text-[#ec4899]">#</span>about-me
          </router-link>

          <button @click="toggleTheme" :class="navText" class="text-start">
            {{ theme === "dark" ? "☀️ Light Mode" : "🌙 Dark Mode" }}
          </button>

          <div class="border-t border-[#ec4899]/40 pt-4">
            <p class="text-xs text-[#d1d5db] mb-2">Language</p>
            <button :class="navText" class="me-2">EN</button>
            <button :class="navText">KH</button>
          </div>

        </div>
      </div>

  </header>
</template>
