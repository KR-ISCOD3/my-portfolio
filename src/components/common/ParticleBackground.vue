<template>
  <div ref="container" class="fixed inset-0 -z-10 transition-opacity duration-300" :class="visible ? 'opacity-100' : 'opacity-0'"></div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount, watch } from "vue"
import { tsParticles } from "@tsparticles/engine"
import { loadSlim } from "@tsparticles/slim"
import { useTheme } from "../../composables/useTheme"

const container = ref(null)
const visible = ref(true)
let instance = null
const { theme } = useTheme()

const getOptions = (mode) => ({
  background: { color: mode === "dark" ? "rgb(27,27,27)" : "#f8fafc" },
  fpsLimit: 120,
  interactivity: {
    events: { onHover: { enable: true, mode: "grab" }, resize: true },
    modes: { grab: { distance: 300, links: { opacity: 0.5 } } },
  },
  particles: {
    number: { value: 60, density: { enable: true, area: 800 } },
    color: { value: mode === "dark" ? "#FFB6C1" : "#ec4899" },
    links: {
      enable: true,
      color: mode === "dark" ? "#FFB6C1" : "#ec4899",
      distance: 150,
      opacity: 0.5,
      width: 2,
    },
    move: { enable: true, speed: 2, outModes: { default: "bounce" } },
    opacity: { value: 1 },
    size: { value: { min: 1, max: 4 } },
  },
  detectRetina: true,
})

const loadParticles = async () => {
  visible.value = false
  await new Promise(r => setTimeout(r, 200))

  instance?.destroy()
  instance = await tsParticles.load({
    element: container.value,
    options: getOptions(theme.value),
  })

  visible.value = true
}

onMounted(async () => {
  await loadSlim(tsParticles)
  await loadParticles()
})

watch(theme, loadParticles)

onBeforeUnmount(() => instance?.destroy())
</script>
