<template>
  <div class="relative h-screen overflow-hidden">
    <!-- INTRO SCREEN -->
    <div class="hero absolute inset-0 flex items-center justify-center">
      <div class="text-center">
        <div class="flex items-baseline justify-center space-x-4 mb-6">
          <h2 class="intro text-5xl serif-font">hi, i'm</h2>
          <h1 class="name text-7xl font-bold text-(--info)">agnes.</h1>
        </div>

        <p class="desc text-xl">i'm exploring web design and anything related to art.</p>
      </div>
    </div>

    <div class="homepage topbar absolute top-0 right-0 flex items-center px-10 py-6 opacity-0">
      <Homepage />
    </div>
  </div>
</template>

<script setup lang="ts">
// @ts-ignore: some .vue modules may lack a default export in TS typings; runtime default exists
import Homepage from './homepage.vue'
import { gsap } from 'gsap'
import { onMounted } from 'vue'

onMounted(() => {
  const tl = gsap.timeline()

  tl.from('.intro', {
    x: -40,
    opacity: 0,
    duration: 1,
  })
    .from('.name', {
      x: 40,
      opacity: 0,
      duration: 1,
    })
    .from('.desc', {
      y: 20,
      opacity: 0,
      duration: 0.8,
    })
    .to({}, { duration: 1 })
    .to('.intro', {
      opacity: 0,
      y: -20,
      duration: 0.5,
    })
    .to(
      '.desc',
      {
        opacity: 0,
        y: 20,
        duration: 0.5,
      },
      '<',
    )

    .to('.name', {
      duration: 1.2,
      scale: 0.5,
      ease: 'power3.inOut',

      x: () => {
        const name = document.querySelector('.name') as HTMLElement
        const rect = name.getBoundingClientRect()

        // same horizontal padding as navbar
        return 40 - rect.left
      },

      y: () => {
        const name = document.querySelector('.name') as HTMLElement
        const rect = name.getBoundingClientRect()

        // same vertical padding as navbar
        return 24 - rect.top
      },
    })

    .to('.homepage', {
      opacity: 1,
      duration: 1,
    })
})
</script>

<style scoped></style>

<!-- .from('.name', {...}, '-=0.5') this is to create a delay in the next animation. this one specifically starts the next animation 0.5 secs before the one previous ends-->
