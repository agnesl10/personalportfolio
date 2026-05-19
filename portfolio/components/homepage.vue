<template>
  <div class="relative h-screen">
    <Navbar />

    <div class="absolute right-[10%] top-1/2 -translate-y-1/2">
      <div class="relative w-[750px] max-w-none">
        <div class="absolute z-0 overflow-hidden left-[10%] top-[10%] w-[63%] h-[80%] rotate-10">
          <img src="/photo1.jpeg" class="w-full h-full object-cover" />
        </div>

        <img src="/digicam.png" class="relative z-10 w-full max-w-none block rotate-10" />
      </div>
    </div>

    <div class="absolute inset-y-0 left-[10%] flex items-center">
      <div class="flex flex-col items-start text-left">
        <h2 class="text-6xl serif-font leading-none">hi, i'm</h2>

        <h1 class="text-8xl title-font text-(--info) leading-none mt-2">agnes.</h1>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import Navbar from './navbar.vue'
</script>
