<template>
  <div class="bg-gray-900">
    <section class="relative py-20 overflow-hidden">
      <div class="container mx-auto px-6 mt-20">
        <div class="max-w-3xl">
          <h1 class="text-4xl md:text-6xl font-bold mb-6">
            Marketingové Balíčky
          </h1>
          <p class="text-xl text-gray-400 mb-8">
            Komplexní marketingové balíčky pro růst vašeho podnikání
          </p>
        </div>
      </div>
    </section>

    <!-- Bundles Grid -->
    <section class="py-20">
      <div class="container mx-auto px-6">
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
          <div v-for="bundle in bundles" :key="bundle.title"
               class="flex flex-col p-6 rounded-lg border border-4 border-gray-800 hover:border-customRed transition-colors">
            <div class="aspect-video mb-6">
              <NuxtImg 
                :src="bundle.image" 
                class="rounded-lg w-full h-64 object-cover"
                width="400"
                height="300"
                :alt="bundle.title"
              />
            </div>
            <div>
              <h3 class="text-2xl font-bold mb-4">{{ bundle.title }}</h3>
              <p class="text-gray-400 mb-6">{{ bundle.description }}</p>
              <ul class="space-y-3 mb-6">
                <li v-for="feature in bundle.features" :key="feature"
                    class="flex items-center text-gray-300">
                  <Icon name="heroicons:check-circle" class="w-5 h-5 text-customRed mr-2" />
                  {{ feature }}
                </li>
              </ul>
              <NuxtLink :to="bundle.link"
                       class="inline-flex items-center text-customRed hover:text-customRed2 transition-colors">
                Zjistit více
                <Icon name="heroicons:arrow-right" class="w-4 h-4 ml-2" />
              </NuxtLink>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
const bundles = [
  {
    title: 'Profesionální Focení',
    description: 'Vysoce kvalitní fotografie pro prezentaci vašich produktů a značky.',
    image: 'https://picsum.photos/id/3/800/600',
    features: [
      'Profesionální vybavení',
      'Focení v ateliéru nebo na místě',
      'Včetně post-processingu',
      'Více úhlů a nastavení'
    ],
    link: '/bundles/photoshoot'
  },
  {
    title: 'Tvorba Webových Stránek',
    description: 'Zakázkový design a vývoj webových stránek pro vaše podnikání.',
    image: 'https://picsum.photos/id/2/800/600',
    features: [
      'Responzivní design',
      'SEO optimalizace',
      'Redakční systém',
      'Integrace analytiky'
    ],
    link: '/bundles/website'
  },
  {
    title: 'Marketing na Sociálních Sítích',
    description: 'Strategické kampaně na sociálních sítích pro posílení vaší online přítomnosti.',
    image: 'https://picsum.photos/id/4/800/600',
    features: [
      'Tvorba obsahu',
      'Strategie engagementu',
      'Analytika a reportování',
      'Optimalizace platforem'
    ],
    link: '/bundles/social-media'
  },
  {
    title: 'Správa Sociálních Sítí',
    description: 'Průběžná správa a optimalizace vašich účtů na sociálních sítích.',
    image: 'https://picsum.photos/id/5/800/600',
    features: [
      'Každodenní správa příspěvků',
      'Komunikace s komunitou',
      'Obsahový kalendář',
      'Sledování výkonu'
    ],
    link: '/bundles/social-management'
  },
  {
    title: 'Nastavení Reklamních Kampaní',
    description: 'Profesionální nastavení vašich reklamních kampaní napříč platformami.',
    image: 'https://picsum.photos/id/6/800/600',
    features: [
      'Výběr platforem',
      'Cílení na publikum',
      'Kreativní design',
      'Struktura kampaně'
    ],
    link: '/bundles/ads-setup'
  },
  {
    title: 'Správa Reklamních Kampaní',
    description: 'Průběžná optimalizace a správa vašich reklamních kampaní.',
    image: 'https://picsum.photos/id/7/800/600',
    features: [
      'Monitoring výkonu',
      'Optimalizace rozpočtu',
      'A/B testování',
      'Sledování ROI'
    ],
    link: '/bundles/ads-management'
  }
]
</script> 