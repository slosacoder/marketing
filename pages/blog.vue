<template>
  <div class="bg-gray-900">
    <!-- Hero Section -->
    <section class="relative py-20 overflow-hidden">
      <div class="container mx-auto px-6 mt-20">
        <div class="max-w-3xl">
          <h1 class="text-4xl md:text-6xl font-bold mb-6">
            Marketingové Postřehy
          </h1>
          <p class="text-xl text-gray-400 mb-8">
            Nejnovější trendy, strategie a poznatky v digitálním marketingu
          </p>
        </div>
      </div>
    </section>

    <!-- Featured Post -->
    <section class="py-1 bg-gray-900">
      <div class="container mx-auto px-6">
        <div class="grid md:grid-cols-2 gap-8 items-center bg-gray-800/30 rounded-2xl p-8">
          <div class="aspect-w-16 aspect-h-9">
            <NuxtImg 
              :src="featuredPost.image" 
              class="w-full h-full object-cover rounded-lg"
              width="800"
              height="450"
              :alt="featuredPost.title"
            />
          </div>
          <div>
            <span class="text-customRed text-sm font-medium mb-2 inline-block">
              {{ featuredPost.category }}
            </span>
            <h2 class="text-2xl md:text-3xl font-bold mb-4">
              {{ featuredPost.title }}
            </h2>
            <p class="text-gray-400 mb-6">{{ featuredPost.excerpt }}</p>
            <div class="flex items-center gap-4 mb-6">
              <NuxtImg 
                :src="featuredPost.author.avatar" 
                class="w-10 h-10 rounded-full"
                width="40"
                height="40"
                :alt="featuredPost.author.name"
              />
              <div>
                <p class="font-medium">{{ featuredPost.author.name }}</p>
                <p class="text-sm text-gray-400">{{ featuredPost.date }}</p>
              </div>
            </div>
            <NuxtLink :to="featuredPost.link" 
                     class="inline-flex items-center text-customRed hover:text-customRed2 transition-colors">
              Číst více
              <Icon name="heroicons:arrow-right" class="w-4 h-4 ml-2" />
            </NuxtLink>
          </div>
        </div>
      </div>
    </section>

    <!-- Main Content -->
    <section class="py-12 bg-gray-900">
      <div class="container mx-auto px-6">
        <div class="flex flex-col lg:flex-row gap-12">
          <!-- Articles Grid -->
          <div class="flex-1">
            <!-- Search and Filters -->
            <div class="mb-8 flex gap-4">
              <div class="relative flex-1">
                <Icon name="heroicons:magnifying-glass" class="absolute left-4 top-3.5 w-5 h-5 text-gray-400" />
                <input 
                  v-model="searchQuery"
                  type="text"
                  placeholder="Hledat články..."
                  class="w-full pl-12 pr-4 py-3 bg-gray-800/50 rounded-lg text-white placeholder:text-gray-400 focus:outline-none focus:ring-2 focus:ring-customRed"
                />
              </div>
              <select 
                v-model="selectedCategory"
                class="px-4 py-3 bg-gray-800/50 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-customRed"
              >
                <option value="all">Všechny kategorie</option>
                <option v-for="category in categories" :key="category" :value="category">
                  {{ category }}
                </option>
              </select>
            </div>

            <!-- Articles -->
            <div class="grid gap-8">
              <article v-for="post in filteredPosts" :key="post.id"
                      class="flex flex-col md:flex-row gap-6 p-6 bg-gray-800/30 rounded-lg">
                <div class="md:w-1/3">
                  <NuxtImg 
                    :src="post.image" 
                    class="w-full h-48 object-cover rounded-lg"
                    width="300"
                    height="200"
                    :alt="post.title"
                  />
                </div>
                <div class="md:w-2/3">
                  <span class="text-customRed text-sm font-medium mb-2 inline-block">
                    {{ post.category }}
                  </span>
                  <h3 class="text-xl font-bold mb-3">{{ post.title }}</h3>
                  <p class="text-gray-400 mb-4">{{ post.excerpt }}</p>
                  <div class="flex items-center justify-between">
                    <div class="flex items-center gap-3">
                      <NuxtImg 
                        :src="post.author.avatar" 
                        class="w-8 h-8 rounded-full"
                        width="32"
                        height="32"
                        :alt="post.author.name"
                      />
                      <span class="text-sm text-gray-400">{{ post.author.name }}</span>
                    </div>
                    <span class="text-sm text-gray-400">{{ post.date }}</span>
                  </div>
                  <NuxtLink :to="post.link" 
                           class="inline-flex pt-2 items-center text-customRed hover:text-customRed2 transition-colors">
                    Číst více
                    <Icon name="heroicons:arrow-right" class="w-4 h-4 ml-2" />
                  </NuxtLink>
                </div>
              </article>
            </div>
          </div>

          <!-- Sidebar -->
          <div class="lg:w-80 space-y-8">
            <!-- Categories -->
            <div class="p-6 bg-gray-800/30 rounded-lg">
              <h3 class="text-lg font-bold mb-4">Kategorie</h3>
              <ul class="space-y-2">
                <li v-for="category in categories" :key="category">
                  <button 
                    @click="selectedCategory = category"
                    class="text-gray-400 hover:text-customRed transition-colors"
                  >
                    {{ category }}
                  </button>
                </li>
              </ul>
            </div>

            <!-- Newsletter -->
            <div class="p-6 bg-gray-800/30 rounded-lg">
              <h3 class="text-lg font-bold mb-4">Přihlaste se k odběru</h3>
              <p class="text-gray-400 text-sm mb-4">
                Získejte nejnovější marketingové poznatky přímo do vaší schránky.
              </p>
              <input 
                type="email"
                placeholder="Zadejte váš email"
                class="w-full px-4 py-2 mb-4 bg-gray-800/50 rounded-lg text-white placeholder:text-gray-400 focus:outline-none focus:ring-2 focus:ring-customRed"
              />
              <button class="w-full px-4 py-2 bg-customRed text-white font-medium rounded-lg hover:bg-customRed2 transition-colors">
                Odebírat
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
const categories = ['Marketingová Strategie', 'Sociální Média', 'Content Marketing', 'SEO', 'Analytika']
const searchQuery = ref('')
const selectedCategory = ref('all')

const featuredPost = {
  title: 'Budoucnost Digitálního Marketingu v 2024',
  excerpt: 'Objevte nové trendy a technologie, které formují budoucnost digitálního marketingu.',
  image: 'https://picsum.photos/id/60/800/450',
  category: 'Marketingová Strategie',
  author: {
    name: 'Emma Williams',
    avatar: 'https://picsum.photos/id/66/100/100'
  },
  date: '15. března 2024',
  link: '/blog/future-of-digital-marketing'
}

const posts = [
  {
    id: 1,
    title: 'Jak zvládnout Marketing na Sociálních Sítích',
    excerpt: 'Naučte se základní strategie pro efektivní marketingové kampaně na sociálních sítích.',
    image: 'https://picsum.photos/id/61/600/400',
    category: 'Sociální Média',
    author: {
      name: 'Michael Chen',
      avatar: 'https://picsum.photos/id/65/100/100'
    },
    date: '12. března 2024'
  },
  {
    id: 2,
    title: 'Nejlepší SEO Praktiky pro rok 2024',
    excerpt: 'Buďte před konkurencí s těmito osvědčenými SEO strategiemi.',
    image: 'https://picsum.photos/id/62/600/400',
    category: 'SEO',
    author: {
      name: 'Sarah Johnson',
      avatar: 'https://picsum.photos/id/64/100/100'
    },
    date: '10. března 2024'
  },
  {
    id: 3,
    title: 'Strategie Content Marketingu',
    excerpt: 'Vytvářejte poutavý obsah, který zvyšuje engagement a konverze.',
    image: 'https://picsum.photos/id/63/600/400',
    category: 'Content Marketing',
    author: {
      name: 'James Wilson',
      avatar: 'https://picsum.photos/id/67/100/100'
    },
    date: '8. března 2024'
  }
]

const filteredPosts = computed(() => {
  return posts.filter(post => {
    const matchesSearch = post.title.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
                         post.excerpt.toLowerCase().includes(searchQuery.value.toLowerCase())
    const matchesCategory = selectedCategory.value === 'all' || 
                           post.category === selectedCategory.value
    return matchesSearch && matchesCategory
  })
})
</script> 