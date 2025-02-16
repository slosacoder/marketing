<template>
  <header class="fixed top-4 left-0 w-full h-20 z-50">
    <div class="mx-4 px-6 h-full flex items-center justify-between bg-black/50 backdrop-blur-lg max-w-4xl lg:mx-auto" 
         :class="[isMenuOpen ? 'rounded-t-2xl' : 'rounded-2xl']">
      <!-- Logo -->
      <div class="text-2xl font-bold">
        <NuxtLink to="/" class="text-white">
          MARKETING ONE
        </NuxtLink>
      </div>

      <!-- Desktop Navigation -->
      <nav class="hidden md:flex items-center space-x-8">
        <NuxtLink 
          v-for="item in navItems" 
          :key="item.text"
          :to="'/' + item.url"
          class="text-sm font-medium hover:text-customRed transition-colors"
        >
          {{ item.text }}
        </NuxtLink>
      </nav>

      <!-- Mobile Menu Button -->
      <button 
        class="md:hidden text-white p-2"
        @click="isMenuOpen = !isMenuOpen"
      >
        <Icon 
          :name="isMenuOpen ? 'heroicons:x-mark' : 'heroicons:bars-3'" 
          class="w-6 h-6"
        />
      </button>

      <!-- Contact Button (Desktop) -->
      <button class="hidden md:block px-6 py-2 bg-customRed text-white text-sm font-medium rounded hover:bg-customRed2 transition-colors">
        <NuxtLink to="/contact" class="text-white">
          KONTAKT
        </NuxtLink>
      </button>
    </div>

    <!-- Mobile Menu -->
    <div 
      v-show="isMenuOpen"
      class="md:hidden absolute -mt-[1px] mx-4 bg-black/50 backdrop-blur-lg rounded-b-2xl max-w-4xl lg:mx-auto w-[calc(100%-2rem)]"
    >
      <div class="px-6 py-4">
        <nav class="flex flex-col space-y-4">
          <NuxtLink
            v-for="item in navItems"
            :key="item.text"
            :to="'/' + item.url"
            class="text-sm font-medium hover:text-customRed transition-colors py-2"
            @click="isMenuOpen = false"
          >
            {{ item.text }}
          </NuxtLink>
          <button class="px-6 py-2 bg-customRed text-white text-sm font-medium rounded hover:bg-customRed2 transition-colors w-full mt-4">
            <NuxtLink to="/contact" class="text-white">
              KONTAKT
            </NuxtLink>
          </button>
        </nav>
      </div>
    </div>
  </header>
</template>

<script setup lang="ts">
const navItems = [
  { text: 'BALÍČKY', url: 'bundles' },
  { text: 'O NÁS', url: 'company' },
  { text: 'BLOG', url: 'blog' }
]
const isMenuOpen = ref(false)

// Close menu when clicking outside
onMounted(() => {
  document.addEventListener('click', (event) => {
    const header = document.querySelector('header')
    if (header && !header.contains(event.target as Node)) {
      isMenuOpen.value = false
    }
  })
})

// Close menu on route change
watch(() => useRoute().path, () => {
  isMenuOpen.value = false
})

// Close menu when resizing to desktop view
onMounted(() => {
  window.addEventListener('resize', () => {
    if (window.innerWidth >= 768) { // md breakpoint
      isMenuOpen.value = false
    }
  })
})

// Prevent scrolling when menu is open
watch(isMenuOpen, (value) => {
  if (value) {
    document.body.style.overflow = 'hidden'
  } else {
    document.body.style.overflow = ''
  }
})

// Cleanup
onBeforeUnmount(() => {
  document.body.style.overflow = ''
})
</script> 