<template>
  <section id="projects" class="py-28 bg-slate-50">
    <div class="max-w-6xl mx-auto px-6">
      <div class="text-center mb-16">
        <p class="text-indigo-600 font-semibold text-sm tracking-widest uppercase mb-3">Portofolio</p>
        <h2 class="text-4xl md:text-5xl font-black text-slate-900">Proyek</h2>
        <p class="text-slate-500 mt-4 max-w-lg mx-auto">Dikerjakan dengan</p>
      </div>

      <!-- Filter tabs -->
      <div class="flex flex-wrap justify-center gap-3 mb-12">
        <button
          v-for="tag in filterTags"
          :key="tag"
          @click="activeFilter = tag"
          :class="[
            'px-5 py-2 rounded-full text-sm font-semibold transition-all duration-200',
            activeFilter === tag
              ? 'bg-indigo-600 text-white shadow-lg shadow-indigo-200'
              : 'bg-white text-slate-500 ring-1 ring-slate-200 hover:ring-indigo-300 hover:text-indigo-600'
          ]"
        >
          {{ tag }}
        </button>
      </div>

      <!-- Projects grid -->
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div
          v-for="project in filteredProjects"
          :key="project.title"
          class="bg-white rounded-3xl overflow-hidden ring-1 ring-slate-100 hover:ring-indigo-200 hover:shadow-xl hover:shadow-indigo-50 transition-all duration-300 group hover:-translate-y-1"
        >
          <!-- Project thumbnail -->
          <div :class="['h-48 flex items-center justify-center relative overflow-hidden', project.bg]">
            <img
               :src="project.image"
               :alt="project.title"
              class="w-full h-full object-cover"
            />
            <div class="absolute top-3 right-3">
              <span class="text-xs font-bold bg-white/90 text-slate-600 px-3 py-1 rounded-full">{{ project.type }}</span>
            </div>
          </div>

          <div class="p-6">
            <h3 class="font-bold text-slate-900 text-lg mb-2 group-hover:text-indigo-600 transition-colors">{{ project.title }}</h3>
            <p class="text-slate-500 text-sm leading-relaxed mb-4">{{ project.desc }}</p>

            <div class="flex flex-wrap gap-2 mb-5">
              <span v-for="tech in project.techs" :key="tech"
                class="text-xs bg-indigo-50 text-indigo-600 font-medium px-2.5 py-1 rounded-full">
                {{ tech }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'
import nodeLogo from '@/assets/nodejs.jpg'
import vueLogo from '@/assets/vuejs.jpg'
import figmaLogo from '@/assets/figma.jpg'
import tailwindcssLogo from '@/assets/tailwindcss.jpg'

const activeFilter = ref('Semua')
const filterTags = ['Semua', 'Vue.js', 'Node.js', 'Tailwind css', 'figma']

const projects = [
 {
  title: 'Node.js',
  image: nodeLogo,
  desc: 'abcdefghijklmnop',
  bg: 'bg-gradient-to-br from-pink-100 to-rose-50',
  type: 'Node.js',
  tags: ['Node.js'],
},

 {
  title: 'vue.js',
  image: vueLogo,
  desc: 'abcdefghijklmnop',
  bg: 'bg-gradient-to-br from-pink-100 to-rose-50',
  type: 'Vue.js',
  tags: ['Vue.js'],
},

 {
  title: 'Figma',
  image: figmaLogo,
  desc: 'abcdefghijklmnop',
  bg: 'bg-gradient-to-br from-pink-100 to-rose-50',
  type: 'Figma',
  tags: ['Figma'],
},

 {
  title: 'tailwindcss',
  image: tailwindcssLogo,
  desc: 'abcdefghijklmnop',
  bg: 'bg-gradient-to-br from-pink-100 to-rose-50',
  type: 'tailwindcss',
  tags: ['Tailwind css'],
}

]

const filteredProjects = computed(() =>
  activeFilter.value === 'Semua'
    ? projects
    : projects.filter(p => p.tags.includes(activeFilter.value))
)
</script>
