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
      <Navbar />
    </div>
  </div>
</template>

<script setup lang="ts">
import Navbar from './navbar.vue'
import { gsap } from 'gsap'
import { onMounted } from 'vue'

onMounted(() => {
  const tl = gsap.timeline()

  // intro animations
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

    // wait a second
    .to({}, { duration: 1 })

    // fade intro + desc out
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

    // move name to top left
    .to(
      '.name',
      {
        x: -667,
        y: -400,
        scale: 0.5,
        duration: 1.2,
        ease: 'power3.inOut',
      },
      '-=0.2',
    )

    // reveal homepage
    .to('.homepage', {
      opacity: 1,
      duration: 1,
    })
})
</script>

<style scoped></style>

<!-- .from('.name', {...}, '-=0.5') this is to create a delay in the next animation. this one specifically starts the next animation 0.5 secs before the one previous ends-->
