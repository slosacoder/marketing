<template>
  <div>
    <!-- Hero Section -->
    <section class="relative py-20 overflow-hidden bg-black/30">
      <div class="container mx-auto px-6">
        <div class="max-w-3xl">
          <h1 class="text-4xl md:text-6xl font-bold mb-6">
            Join Our Team
          </h1>
          <p class="text-xl text-gray-400 mb-8">
            Be part of a dynamic team shaping the future of digital marketing
          </p>
        </div>
      </div>
    </section>

    <!-- Job Listings -->
    <section class="py-20">
      <div class="container mx-auto px-6">
        <!-- Search and Filter -->
        <div class="mb-12 flex flex-col md:flex-row gap-4">
          <div class="relative flex-1">
            <Icon name="heroicons:magnifying-glass" class="absolute left-4 top-3.5 w-5 h-5 text-gray-400" />
            <input 
              v-model="searchQuery"
              type="text"
              placeholder="Search positions..."
              class="w-full pl-12 pr-4 py-3 bg-gray-800/50 rounded-lg text-white placeholder:text-gray-400 focus:outline-none focus:ring-2 focus:ring-customRed"
            />
          </div>
          <select 
            v-model="selectedDepartment"
            class="px-4 py-3 bg-gray-800/50 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-customRed"
          >
            <option value="all">All Departments</option>
            <option v-for="dept in departments" :key="dept" :value="dept">
              {{ dept }}
            </option>
          </select>
        </div>

        <!-- Jobs Grid -->
        <div class="grid gap-6">
          <div v-for="job in filteredJobs" :key="job.id"
               class="p-6 bg-gray-800/30 rounded-lg hover:bg-gray-800/50 transition-colors">
            <div class="flex flex-col md:flex-row justify-between gap-4">
              <div>
                <h3 class="text-xl font-bold mb-2">{{ job.title }}</h3>
                <div class="flex flex-wrap gap-3 mb-4">
                  <span class="px-3 py-1 bg-gray-700 rounded-full text-sm">{{ job.department }}</span>
                  <span class="px-3 py-1 bg-gray-700 rounded-full text-sm">{{ job.location }}</span>
                  <span class="px-3 py-1 bg-gray-700 rounded-full text-sm">{{ job.type }}</span>
                </div>
                <p class="text-gray-400">{{ job.description }}</p>
              </div>
              <div class="flex items-start">
                <button class="px-6 py-2 bg-customRed text-white rounded hover:bg-customRed2 transition-colors whitespace-nowrap">
                  Apply Now
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Benefits Section -->
    <section class="py-20 bg-black/30">
      <div class="container mx-auto px-6">
        <h2 class="text-3xl font-bold text-center mb-12">Why Join Us?</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div v-for="benefit in benefits" :key="benefit.title"
               class="p-6 rounded-lg">
            <Icon :name="benefit.icon" class="w-12 h-12 text-customRed mb-4" />
            <h3 class="text-xl font-bold mb-4">{{ benefit.title }}</h3>
            <p class="text-gray-400">{{ benefit.description }}</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
const departments = ['Marketing', 'Design', 'Development', 'Sales', 'Customer Success']
const searchQuery = ref('')
const selectedDepartment = ref('all')

const jobs = [
  {
    id: 1,
    title: 'Senior Marketing Strategist',
    department: 'Marketing',
    location: 'Remote',
    type: 'Full-time',
    description: 'Lead the development and execution of marketing strategies for our key clients.'
  },
  {
    id: 2,
    title: 'UI/UX Designer',
    department: 'Design',
    location: 'New York',
    type: 'Full-time',
    description: 'Create beautiful and intuitive user interfaces for our digital marketing platforms.'
  },
  {
    id: 3,
    title: 'Frontend Developer',
    department: 'Development',
    location: 'Remote',
    type: 'Full-time',
    description: 'Build responsive and performant web applications using modern technologies.'
  }
]

const benefits = [
  {
    title: 'Remote First',
    icon: 'heroicons:home',
    description: 'Work from anywhere in the world with our flexible remote policy.'
  },
  {
    title: 'Growth Opportunities',
    icon: 'heroicons:academic-cap',
    description: 'Continuous learning and career development programs.'
  },
  {
    title: 'Great Benefits',
    icon: 'heroicons:heart',
    description: 'Comprehensive health coverage, 401k matching, and more.'
  }
]

const filteredJobs = computed(() => {
  return jobs.filter(job => {
    const matchesSearch = job.title.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
                         job.description.toLowerCase().includes(searchQuery.value.toLowerCase())
    const matchesDepartment = selectedDepartment.value === 'all' || 
                             job.department === selectedDepartment.value
    return matchesSearch && matchesDepartment
  })
})
</script> 