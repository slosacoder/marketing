<template>
  <div class="bg-gray-900">
    <!-- Hero Section -->
    <section class="relative py-20 overflow-hidden">
      <div class="container mx-auto px-6 mt-20">
        <div class="max-w-3xl">
          <h1 class="text-4xl md:text-6xl font-bold mb-6">
            Náš příběh
          </h1>
          <p class="text-xl text-gray-400 mb-8">
            Budujeme budoucnost digitálního marketingu pomocí inovací a odborných znalostí
          </p>
        </div>
      </div>
    </section>

    <!-- Values Section -->
    <section class="py-1 bg-gray-900">
      <div class="container mx-auto px-6">
        <h2 class="text-3xl font-bold text-center mb-12">Naše hodnoty</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div v-for="value in values" :key="value.title"
               class="p-8 bg-gray-800/30 rounded-lg text-center">
            <Icon :name="value.icon" class="w-16 h-16 text-customRed mb-6 mx-auto" />
            <h3 class="text-xl font-bold mb-4">{{ value.title }}</h3>
            <p class="text-gray-400">{{ value.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Team Section -->
    <section class="py-20 bg-gray-900">
      <div class="container mx-auto px-6">
        <h2 class="text-3xl font-bold text-center mb-12">Náš tým</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div v-for="member in team" :key="member.name"
               class="group relative">
            <div class="aspect-w-1 aspect-h-1 mb-4">
              <NuxtImg 
                :src="member.image" 
                class="w-full h-full object-cover rounded-lg"
                width="300"
                height="300"
                :alt="member.name"
              />
            </div>
            <h3 class="text-lg font-bold">{{ member.name }}</h3>
            <p class="text-customRed mb-2">{{ member.position }}</p>
            <p class="text-gray-400 text-sm">{{ member.bio }}</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
const values = [
  {
    title: 'Inovace',
    icon: 'heroicons:light-bulb',
    description: 'Překračujeme hranice a využíváme nové technologie k poskytování špičkových řešení.'
  },
  {
    title: 'Kvalita',
    icon: 'heroicons:star',
    description: 'Zavázali jsme se poskytovat nejvyšší kvalitu ve všem, co děláme.'
  },
  {
    title: 'Spolupráce',
    icon: 'heroicons:users',
    description: 'Společně pracujeme na dosažení výjimečných výsledků pro naše klienty.'
  }
]

const team = [
  {
    name: 'Sarah Johnson',
    position: 'CEO & Zakladatelka',
    image: 'https://picsum.photos/id/64/300/300',
    bio: 'Marketingová veteránka s více než 15 lety zkušeností v digitální transformaci.'
  },
  {
    name: 'Michael Chen',
    position: 'CTO',
    image: 'https://picsum.photos/id/65/300/300',
    bio: 'Technologický inovátor specializující se na marketingovou automatizaci a AI.'
  },
  {
    name: 'Emma Williams',
    position: 'Kreativní ředitelka',
    image: 'https://picsum.photos/id/66/300/300',
    bio: 'Oceňovaná designérka s vášní pro vyprávění příběhů značek.'
  },
  {
    name: 'James Wilson',
    position: 'Vedoucí strategie',
    image: 'https://picsum.photos/id/67/300/300',
    bio: 'Marketingový stratég zaměřený na růst a inovace.'
  }
]
</script> 