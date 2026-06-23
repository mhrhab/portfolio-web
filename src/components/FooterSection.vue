<template>
  <footer class="bg-slate-900 text-white py-12">
    <div class="max-w-6xl mx-auto px-6">
      <div class="flex flex-col md:flex-row items-center justify-between gap-6">
        <div class="text-center md:text-left">
          <a href="#hero" class="font-bold text-xl tracking-tight">
            <span class="text-indigo-400">&lt;</span>M.habib<span class="text-indigo-400">/&gt;</span>
          </a>
          <p class="text-slate-400 text-sm mt-1">Frontend Developer · Medan, Indonesia</p>
        </div>

        <div class="flex flex-wrap justify-center gap-6 text-sm text-slate-400">
          <a v-for="link in links" :key="link.href" :href="link.href"
            class="hover:text-indigo-400 transition-colors">{{ link.label }}</a>
        </div>

        <p class="text-slate-500 text-sm text-center md:text-right">
          © {{ year }} portofolio. Dibuat dengan Vue.js
        </p>
      </div>
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()
const links = [
  { href: '#about', label: 'About' },
  { href: '#skills', label: 'Skills' },
  { href: '#projects', label: 'Projects' },
  { href: '#contact', label: 'Contact' },
]
</script>
