
<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>

<script setup lang="ts">
// Set dark mode and custom styles
useHead({
  htmlAttrs: {
    class: 'dark bg-black'
  }
})
</script>

