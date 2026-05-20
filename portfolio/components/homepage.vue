<template>
  <div class="relative">
    <!-- NAVBAR (completely independent) -->
    <div class="fixed top-0 left-0 w-full z-50">
      <Navbar />
    </div>

    <!-- SCROLL AREA -->
    <div ref="section" class="h-[300vh] pt-20">
      <!-- PINNED SCENE -->
      <div ref="scene" class="h-screen relative overflow-visible">
        <!-- CAMERA (STARTS RIGHT — stable baseline) -->
        <div ref="cameraWrapper" class="absolute top-1/2 right-[10%] -translate-y-1/2">
          <div class="relative w-[750px]">
            <div
              class="absolute z-0 left-[10%] top-[10%] w-[63%] h-[80%] overflow-hidden rotate-10"
            >
              <img :src="currentPhoto" class="w-full h-full object-cover" />
            </div>

            <img src="/digicam.png" class="relative z-10 w-full block rotate-10" />
          </div>
        </div>

        <!-- TEXT (ALWAYS LEFT, NEVER MOVES OFF SCREEN) -->
        <div ref="textWrapper" class="absolute left-[8%] top-1/2 -translate-y-1/2">
          <div class="flex flex-col text-left">
            <h2 class="text-6xl serif-font leading-none">
              {{ subtitle }}
            </h2>

            <h1 class="text-9xl title-font text-(--info) leading-none mt-2">
              {{ title }}
            </h1>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import Navbar from './navbar.vue'
import { ref, onMounted } from 'vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const section = ref()
const scene = ref()
const cameraWrapper = ref()

const currentPhoto = ref('/photo1.jpeg')
const subtitle = ref("hi, i'm")
const title = ref('agnes.')

onMounted(() => {
  if (!section.value || !scene.value || !cameraWrapper.value) return

  const vw = window.innerWidth

  const tl = gsap.timeline({
    scrollTrigger: {
      trigger: section.value,
      start: 'top top',
      end: '+=3000',
      scrub: 1.2,
      pin: scene.value,
      anticipatePin: 1,
    },
  })

  // STEP 1 → 2 (center movement)
  tl.to(cameraWrapper.value, {
    x: -vw * 0.25,
    y: -80,
    ease: 'power2.inOut',
    onStart: () => {
      currentPhoto.value = '/photo2.jpeg'
      subtitle.value = 'my'
      title.value = 'hobbies'
    },
  })

    // STEP 2 → 3 (far left but still visible)
    .to(cameraWrapper.value, {
      x: -vw * 0.55,
      y: 0,
      ease: 'power3.inOut',
      onStart: () => {
        currentPhoto.value = '/photo3.jpeg'
        subtitle.value = 'more'
        title.value = 'about me'
      },
    })
})
</script>
