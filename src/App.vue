<template>
  <div
    class="h-screen w-screen flex items-center justify-center bg-gradient-to-br to-cyan-600 from-blue-500"
  >
    <AppLoader
      :is-full-page="true"
      first-circle-color="#5980e3"
      second-circle-color="#a6baed"
      third-circle-color="#1B4CCA"
    />
  </div>
</template>

<script setup lang="ts">
// Import your library here.
import { AppLoader } from "./lib";
</script>
