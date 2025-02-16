<template>
  <div class="bg-gray-900 min-h-screen">
    <!-- Hero Section -->
    <section class="relative py-20 overflow-hidden">
      <div class="container mx-auto px-6 mt-20">
        <div class="max-w-3xl">
          <h1 class="text-4xl md:text-6xl font-bold mb-6">
            Kontaktujte nás
          </h1>
          <p class="text-xl text-gray-400 mb-8">
            Pojďme probrat, jak můžeme pomoci růstu vašeho podnikání
          </p>
        </div>
      </div>
    </section>

    <!-- Contact Form Section -->
    <section class="py-10">
      <div class="container mx-auto px-6">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
          <!-- Contact Form -->
          <div class="space-y-8">
            <div class="space-y-6">
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div>
                  <label class="block text-sm font-medium mb-2">Jméno</label>
                  <input 
                    type="text"
                    class="w-full px-4 py-3 bg-gray-800/50 rounded-lg text-white placeholder:text-gray-400 focus:outline-none focus:ring-2 focus:ring-customRed"
                    placeholder="Jan"
                  />
                </div>
                <div>
                  <label class="block text-sm font-medium mb-2">Příjmení</label>
                  <input 
                    type="text"
                    class="w-full px-4 py-3 bg-gray-800/50 rounded-lg text-white placeholder:text-gray-400 focus:outline-none focus:ring-2 focus:ring-customRed"
                    placeholder="Novák"
                  />
                </div>
              </div>
              
              <div>
                <label class="block text-sm font-medium mb-2">Email</label>
                <input 
                  type="email"
                  class="w-full px-4 py-3 bg-gray-800/50 rounded-lg text-white placeholder:text-gray-400 focus:outline-none focus:ring-2 focus:ring-customRed"
                  placeholder="jan@example.com"
                />
              </div>

              <div>
                <label class="block text-sm font-medium mb-2">Společnost</label>
                <input 
                  type="text"
                  class="w-full px-4 py-3 bg-gray-800/50 rounded-lg text-white placeholder:text-gray-400 focus:outline-none focus:ring-2 focus:ring-customRed"
                  placeholder="Název vaší společnosti"
                />
              </div>

              <div>
                <label class="block text-sm font-medium mb-2">Zpráva</label>
                <textarea 
                  class="w-full px-4 py-3 bg-gray-800/50 rounded-lg text-white placeholder:text-gray-400 focus:outline-none focus:ring-2 focus:ring-customRed h-32"
                  placeholder="Jak vám můžeme pomoci?"
                ></textarea>
              </div>
            </div>

            <button class="w-full px-8 py-3 bg-customRed text-white font-medium rounded-lg hover:bg-customRed2 transition-colors">
              Odeslat zprávu
            </button>
          </div>

          <!-- Contact Information -->
          <div class="lg:pl-12">
            <div class="space-y-8">
              <div>
                <h3 class="text-2xl font-bold mb-4">Kontaktní informace</h3>
                <p class="text-gray-400">
                  Připraveni posunout váš marketing na další úroveň? Kontaktujte nás přes některý z těchto kanálů.
                </p>
              </div>

              <div class="space-y-4">
                <div class="flex items-start space-x-4">
                  <Icon name="heroicons:map-pin" class="w-6 h-6 text-customRed mt-1" />
                  <div>
                    <h4 class="font-medium mb-1">Navštivte nás</h4>
                    <p class="text-gray-400">123 Marketing Street<br/>New York, NY 10001</p>
                  </div>
                </div>

                <div class="flex items-start space-x-4">
                  <Icon name="heroicons:phone" class="w-6 h-6 text-customRed mt-1" />
                  <div>
                    <h4 class="font-medium mb-1">Zavolejte nám</h4>
                    <p class="text-gray-400">+1 (555) 123-4567</p>
                  </div>
                </div>

                <div class="flex items-start space-x-4">
                  <Icon name="heroicons:envelope" class="w-6 h-6 text-customRed mt-1" />
                  <div>
                    <h4 class="font-medium mb-1">Napište nám</h4>
                    <p class="text-gray-400">contact@marketingone.com</p>
                  </div>
                </div>
              </div>

              <!-- Social Links -->
              <div>
                <h4 class="font-medium mb-4">Sledujte nás</h4>
                <div class="flex space-x-4">
                  <a href="#" class="p-2 bg-gray-800/50 rounded-lg hover:bg-gray-700/50 transition-colors">
                    <Icon name="mdi:twitter" class="w-5 h-5 mt-2" />
                  </a>
                  <a href="#" class="p-2 bg-gray-800/50 rounded-lg hover:bg-gray-700/50 transition-colors">
                    <Icon name="mdi:linkedin" class="w-5 h-5 mt-2" />
                  </a>
                  <a href="#" class="p-2 bg-gray-800/50 rounded-lg hover:bg-gray-700/50 transition-colors">
                    <Icon name="mdi:facebook" class="w-5 h-5 mt-2" />
                  </a>
                  <a href="#" class="p-2 bg-gray-800/50 rounded-lg hover:bg-gray-700/50 transition-colors">
                    <Icon name="mdi:instagram" class="w-5 h-5 mt-2" />
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
// Form handling logic can be added here
</script> 