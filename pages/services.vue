<template>
  <div class="bg-gray-900">
    <!-- Hero Section -->
    <section class="relative py-20 overflow-hidden">
      <div class="container mx-auto px-6 mt-20">
        <div class="max-w-3xl">
          <h1 class="text-4xl md:text-6xl font-bold mb-6">
            Marketing Services That Drive Growth
          </h1>
          <p class="text-xl text-gray-400 mb-8">
            Transform your business with our comprehensive marketing solutions
          </p>
          <button class="px-8 py-3 bg-customRed text-white font-medium rounded-lg hover:bg-customRed2 transition-colors">
            Get Started
          </button>
        </div>
      </div>
    </section>

    <!-- Services Grid -->
    <section class="py-20 bg-gray-900 ">
      <div class="container mx-auto px-6">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div v-for="service in services" :key="service.title"
               class="p-6 rounded-lg border border-4 border-gray-800 hover:border-customRed transition-colors">
            <Icon :name="service.icon" class="w-12 h-12 text-customRed mb-4" />
            <h3 class="text-xl font-bold mb-4">{{ service.title }}</h3>
            <p class="text-gray-400 mb-4">{{ service.description }}</p>
            <NuxtLink :to="service.link"
                     class="text-customRed hover:text-customRed2 transition-colors inline-flex items-center">
              Learn More
              <Icon name="heroicons:arrow-right" class="w-4 h-4 ml-2" />
            </NuxtLink>
          </div>
        </div>
      </div>
    </section>

    <!-- Testimonials -->
    <section class="py-20 bg-gray-900">
      <div class="container mx-auto px-6">
        <h2 class="text-3xl font-bold text-center mb-12">What Our Clients Say</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div v-for="testimonial in testimonials" :key="testimonial.author"
               class="p-6 rounded-lg bg-black/30 backdrop-blur-sm">
            <p class="text-gray-400 mb-4">{{ testimonial.content }}</p>
            <div class="flex items-center">
              <img :src="testimonial.avatar" alt="Avatar" class="w-12 h-12 rounded-full mr-4" />
              <div>
                <h4 class="font-medium">{{ testimonial.author }}</h4>
                <p class="text-sm text-gray-400">{{ testimonial.position }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import BlurredParticleRing from '@/components/features/BlurredParticleRing.vue'

const services = [
  {
    title: 'Digital Marketing',
    icon: 'heroicons:chart-bar',
    description: 'Drive growth through targeted digital marketing campaigns and strategies.',
    link: '/services/digital-marketing'
  },
  {
    title: 'Content Strategy',
    icon: 'heroicons:document-text',
    description: 'Create engaging content that resonates with your target audience.',
    link: '/services/content-strategy'
  },
  {
    title: 'Social Media',
    icon: 'heroicons:share',
    description: 'Build your brand presence across all major social media platforms.',
    link: '/services/social-media'
  }
]

const testimonials = [
  {
    content: "Working with Marketing One transformed our online presence completely.",
    author: "Jane Cooper",
    position: "CEO at TechCorp",
    avatar: "https://picsum.photos/id/64/100/100"
  },
  {
    content: "The results exceeded our expectations. Highly recommended!",
    author: "John Smith",
    position: "Marketing Director",
    avatar: "https://picsum.photos/id/65/100/100"
  },
  {
    content: "Professional team with excellent communication and results.",
    author: "Sarah Johnson",
    position: "Founder at StartupX",
    avatar: "https://picsum.photos/id/66/100/100"
  }
]
</script> 