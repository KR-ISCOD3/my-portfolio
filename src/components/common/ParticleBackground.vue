<template>
  <!-- particle canvas container -->
  <div ref="container" class="fixed inset-0 -z-10 bg-black"></div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue"
import { tsParticles } from "@tsparticles/engine"
import { loadSlim } from "@tsparticles/slim"

const container = ref(null)
let instance = null

onMounted(async () => {
  await loadSlim(tsParticles)

  instance = await tsParticles.load({
    element: container.value,
    options: {
      background: {
        color: "rgb(27,27,27)",
      },
      fpsLimit: 120,
      interactivity: {
        events: {
          onHover: {
            enable: true,
            mode: "grab",
          },
          resize: true,
        },
        modes: {
          grab: {
            distance: 300,
            links: {
              opacity: 0.5,
            },
          },
        },
      },
      particles: {
        number: {
          value: 60,
          density: {
            enable: true,
            area: 800,
          },
        },
        color: {
          value: "#FFB6C1",
        },
        links: {
          enable: true,
          color: "#FFB6C1",
          distance: 150,
          opacity: 0.5,
          width: 2,
        },
        move: {
          enable: true,
          speed: 2,
          outModes: {
            default: "bounce",
          },
        },
        opacity: {
          value: 1,
        },
        size: {
          value: { min: 1, max: 4 },
        },
      },
      detectRetina: true,
    },
  })
})

onBeforeUnmount(() => {
  if (instance) instance.destroy()
})
</script>
