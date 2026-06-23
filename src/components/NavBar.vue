<template>
  <nav
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-300',
      scrolled ? 'bg-white/90 backdrop-blur-md shadow-sm border-b border-slate-100' : 'bg-transparent'
    ]"
  >
    <div class="max-w-6xl mx-auto px-6 py-4 flex items-center justify-between">
      <a href="#hero" class="font-bold text-3xl tracking-tight text-slate-900">
       HABIB
      </a>

      <!-- Desktop Nav -->
      <ul class="hidden md:flex items-center gap-8 text-sm font-medium text-slate-600">
        <li v-for="link in links" :key="link.href">
          <a
            :href="link.href"
            class="hover:text-indigo-600 transition-colors duration-200 relative group"
          >
            {{ link.label }}
            <span class="absolute -bottom-0.5 left-0 w-0 h-0.5 bg-indigo-600 group-hover:w-full transition-all duration-300"></span>
          </a>
        </li>
        <li>
        </li>
      </ul>

      <!-- Mobile Hamburger -->
      <button @click="menuOpen = !menuOpen" class="md:hidden p-2 rounded-lg text-slate-600 hover:text-indigo-600">
        <svg v-if="!menuOpen" class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
        </svg>
        <svg v-else class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
        </svg>
      </button>
    </div>

    <!-- Mobile Menu -->
    <div v-if="menuOpen" class="md:hidden bg-white border-t border-slate-100 px-6 py-4 flex flex-col gap-4">
      <a v-for="link in links" :key="link.href" :href="link.href"
        @click="menuOpen = false"
        class="text-slate-600 hover:text-indigo-600 font-medium transition-colors">
        {{ link.label }}
      </a>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const scrolled = ref(false)
const menuOpen = ref(false)

const links = [
  { href: '#about', label: 'About' },
  { href: '#skills', label: 'Skills' },
  { href: '#projects', label: 'Projects' },
  { href: '#contact', label: 'Contact' },
]

const handleScroll = () => { scrolled.value = window.scrollY > 20 }
onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>
