<template>
  <section id="skills" class="py-28 bg-white">
    <div class="max-w-6xl mx-auto px-6">
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-black text-slate-900">Keahlian <span class="text-indigo-600">Saya</span></h2>
        <p class="text-slate-500 mt-4 max-w-lg mx-auto">Tools dan teknologi yang saya gunakan sehari-hari untuk membangun produk digital.</p>
      </div>

      <!-- Skill categories -->
      <div class="grid md:grid-cols-3 gap-8 mb-14">
        <div v-for="category in skillCategories" :key="category.title"
          class="bg-slate-50 rounded-3xl p-7 ring-1 ring-slate-100 hover:ring-indigo-200 transition-all duration-300">
          <div class="flex items-center gap-3 mb-6">
            <span class="text-2xl">{{ category.icon }}</span>
            <h3 class="font-bold text-slate-800 text-lg">{{ category.title }}</h3>
          </div>
          <div class="flex flex-wrap gap-2">
            <span v-for="skill in category.skills" :key="skill"
              class="px-3 py-1.5 bg-white text-slate-600 text-sm font-medium rounded-full ring-1 ring-slate-200 hover:ring-indigo-400 hover:text-indigo-600 transition-all duration-200 cursor-default">
              {{ skill }}
            </span>
          </div>
        </div>
      </div>

      <!-- Proficiency bars -->
      <h3 class="text-xl font-bold text-slate-800 mb-8 text-center">Tingkat Keahlian</h3>
      <div class="grid md:grid-cols-2 gap-6 max-w-4xl mx-auto">
        <div v-for="skill in proficiencies" :key="skill.name" class="group">
          <div class="flex justify-between items-center mb-2">
            <div class="flex items-center gap-2">
              <span class="text-lg">{{ skill.icon }}</span>
              <span class="font-semibold text-slate-700 text-sm">{{ skill.name }}</span>
            </div>
            <span class="text-xs font-bold text-indigo-600 bg-indigo-50 px-2.5 py-1 rounded-full">{{ skill.level }}%</span>
          </div>
          <div class="h-2.5 bg-slate-100 rounded-full overflow-hidden">
            <div
              class="h-full bg-gradient-to-r from-indigo-500 to-indigo-400 rounded-full transition-all duration-1000 ease-out"
              :style="{ width: animated ? skill.level + '%' : '0%' }"
            ></div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const animated = ref(false)

const skillCategories = [
  {
    icon: '</>', title: 'Frontend',
    skills: ['Vue.js 3','TypeScript', 'Tailwind CSS', 'Vite',]
  },
  {
    icon: '🛠️', title: 'Tools & Workflow',
    skills: ['GitHub', 'Figma', 'VS Code',]
  },
  {
    icon: '⚙️', title: 'Backend & Infra',
    skills: ['Node.js','Supabase', 'Vercel','python',]
  },
]

const proficiencies = [
  { name: 'Vue.js / Nuxt.js', level: 90 },
  { name: 'Tailwind CSS', level: 87 },
  { name: 'JavaScript/typescript', level: 80 },
  { name: 'Python', level: 75 },
  { name: 'Firebase / Supabase', level: 70 },
  { name: 'MongoDB', level: 65 },
]

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) animated.value = true },
    { threshold: 0.3 }
  )
  const section = document.getElementById('skills')
  if (section) observer.observe(section)
})
</script>
