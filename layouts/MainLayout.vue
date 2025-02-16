<template>
  <div class="min-h-screen bg-black">
    <LayoutHeader />
    <main class="pt-20">
      <slot />
    </main>
    <footer class="bg-black/50 backdrop-blur-sm py-12 mt-20">
      <div class="container mx-auto px-6">
        <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
          <div>
            <h3 class="text-xl font-bold mb-4">MARKETING ONE</h3>
            <p class="text-gray-400">Your trusted marketing partner for growth and success.</p>
          </div>
          <!-- Navigation Links -->
          <div v-for="(links, section) in footerLinks" :key="section">
            <h4 class="font-medium mb-4">{{ section }}</h4>
            <ul class="space-y-2">
              <li v-for="link in links" :key="link">
                <NuxtLink :to="link.toLowerCase()" class="text-gray-400 hover:text-customRed transition-colors">
                  {{ link }}
                </NuxtLink>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup lang="ts">
const footerLinks = {
  Company: ['About', 'Careers', 'Contact'],
  Services: ['Marketing', 'Consulting', 'Strategy'],
  Resources: ['Blog', 'Case Studies', 'Documentation']
}
</script> 