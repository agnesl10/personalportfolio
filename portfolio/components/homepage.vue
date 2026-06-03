<template>
  <div class="relative h-screen">
    <Navbar />

    <div class="absolute right-[10%] top-1/2 -translate-y-1/2">...</div>

    <div class="absolute inset-y-0 right-[350%] flex items-center">
      <div class="flex flex-col items-start text-left">
        <h2 class="text-6xl serif-font leading-none text-(--primary)">hi, i'm</h2>

        <h1 class="text-8xl title-font text-(--info) leading-none mt-2">agnes.</h1>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import Navbar from './navbar.vue'
</script>
