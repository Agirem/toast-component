<template>
  <div class="min-h-screen p-4 relative flex flex-col justify-between" :class="isDarkMode ? 'bg-gray-900' : 'bg-gray-50'">
    <!-- Centered Toast Button -->
    <div class="flex-1 flex justify-center items-center">
      <div class="space-y-8 text-center">
        <button
          @click="showToast = true"
          class="px-6 py-3 rounded-lg font-medium transform transition-transform hover:scale-105"
          :class="isDarkMode ? 'bg-white text-black' : 'bg-[#1E293B] text-white hover:bg-[#0F172A]'"
        >
          Afficher le Toast
        </button>

        <!-- Theme Toggle Button -->
        <div class="flex justify-center">
          <button
            @click="toggleTheme"
            class="p-3 rounded-full transform transition-transform hover:scale-105"
            :class="isDarkMode ? 'bg-white text-black' : 'bg-[#1E293B] text-white hover:bg-[#0F172A]'"
          >
            <!-- Sun icon for dark mode -->
            <svg
              v-if="isDarkMode"
              xmlns="http://www.w3.org/2000/svg"
              class="w-6 h-6"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z"
              />
            </svg>
            <!-- Moon icon for light mode -->
            <svg
              v-else
              xmlns="http://www.w3.org/2000/svg"
              class="w-6 h-6"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z"
              />
            </svg>
          </button>
        </div>
      </div>
    </div>

    <!-- Social Links -->
    <div class="flex justify-center gap-6 pb-8">
      <a 
        href="https://github.com/Agirem" 
        target="_blank"
        class="transform transition-transform hover:scale-110"
        :class="isDarkMode ? 'text-white' : 'text-[#1E293B]'"
      >
        <svg class="w-6 h-6" viewBox="0 0 24 24" fill="currentColor">
          <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
        </svg>
      </a>
      <a 
        href="https://x.com/agirem1" 
        target="_blank"
        class="transform transition-transform hover:scale-110"
        :class="isDarkMode ? 'text-white' : 'text-[#1E293B]'"
      >
        <svg class="w-6 h-6" viewBox="0 0 24 24" fill="currentColor">
          <path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/>
        </svg>
      </a>
      <a 
        href="https://linkedin.com/in/agirem1" 
        target="_blank"
        class="transform transition-transform hover:scale-110"
        :class="isDarkMode ? 'text-white' : 'text-[#1E293B]'"
      >
        <svg class="w-6 h-6" viewBox="0 0 24 24" fill="currentColor">
          <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
        </svg>
      </a>
    </div>

    <!-- Toast with Animation -->
    <Transition
      enter-active-class="transform transition ease-out duration-300"
      enter-from-class="translate-y-2 opacity-0 sm:translate-y-0 sm:translate-x-2"
      enter-to-class="translate-y-0 opacity-100 sm:translate-x-0"
      leave-active-class="transition ease-in duration-200"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <div 
        v-if="showToast" 
        class="fixed top-4 right-4"
      >
        <div 
          class="w-[400px] p-4 rounded-lg shadow-lg"
          :class="isDarkMode ? 'bg-slate-900 text-white' : 'bg-white'"
        >
          <div class="flex items-start gap-3">
            <!-- Alert Icon -->
            <div 
              class="w-8 h-8 flex items-center justify-center rounded-lg"
              :style="isDarkMode ? 'background-color: #F1F5F9' : 'background-color: #DBEAFE'"
            >
              <img 
                :src="SubtractIcon" 
                alt="Alert" 
                width="20" 
                height="20" 
                :style="isDarkMode ? 'filter: brightness(0) saturate(100%) invert(13%) sepia(16%) saturate(638%) hue-rotate(182deg) brightness(95%) contrast(88%)' : ''" 
              />
            </div>

            <!-- Content -->
            <div class="flex-1">
              <div class="mb-1 pr-6 font-medium">
                Informations concernants des articles dans votre panier
              </div>
              <div :class="isDarkMode ? 'text-gray-300' : 'text-gray-600'" class="text-sm">
                <p>Des articles ont changé de prix.</p>
                <p><span class="underline">Oppo a baissé, passant de 200€ à 125€</span></p>
              </div>
              <div class="mt-3 flex gap-3">
                <button
                  @click="viewProducts"
                  class="px-4 py-2 text-sm font-medium rounded-lg transition-colors duration-200"
                  :class="isDarkMode ? 'bg-[#0F172A] text-white border border-[#1E293B] hover:bg-[#1E293B]' : 'border border-gray-200 hover:bg-gray-50'"
                >
                  Voir les produits
                </button>
                <button
                  @click="showToast = false"
                  class="px-4 py-2 text-sm font-medium rounded-lg transition-colors duration-200 w-[120px]"
                  :class="isDarkMode ? 'bg-white text-[#0F172A] hover:bg-gray-100' : 'bg-[#1E293B] text-white hover:bg-[#0F172A]'"
                >
                  Fermer
                </button>
              </div>
            </div>

            <!-- Close Button -->
            <button
              @click="showToast = false"
              :class="isDarkMode ? 'text-white hover:text-gray-300' : 'text-gray-500 hover:text-gray-700'"
              class="-mt-1 -mr-1 p-1 transition-colors duration-200"
            >
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <line x1="18" y1="6" x2="6" y2="18"></line>
                <line x1="6" y1="6" x2="18" y2="18"></line>
              </svg>
              <span class="sr-only">Fermer</span>
            </button>
          </div>
        </div>
      </div>
    </Transition>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import SubtractIcon from './assets/icons/Subtract.svg'

const showToast = ref(false)
const isDarkMode = ref(false)

const toggleTheme = () => {
  isDarkMode.value = !isDarkMode.value
}

const viewProducts = () => {
  console.log('Voir les produits clicked')
  showToast.value = false
}
</script>