<template>
  <div class="relative h-screen overflow-hidden">
    <Navbar />

    <div class="absolute right-[14%] top-1/2 -translate-y-1/2 rotate-15">
      <img src="/digicam.png" alt="" class="w-150 md:w-187.5 lg:w-225 xl:w-250" />
    </div>
  </div>
</template>

<script setup lang="ts">
import Navbar from './navbar.vue'
</script>

<style scoped></style>
