<template>
  <section id="about" class="py-28 bg-slate-50">
    <div class="max-w-6xl mx-auto px-6">
      <!-- Header -->
      <div class="text-center mb-16">
        <p class="text-indigo-600 font-semibold text-sm tracking-widest uppercase mb-3">Tentang Saya</p>
        <h2 class="text-4xl md:text-5xl font-black text-slate-900">Siapa <span class="text-indigo-600">Saya?</span></h2>
      </div>

      <div class="grid md:grid-cols-5 gap-12 items-start">
        <!-- Left: Text -->
        <div class="md:col-span-3 space-y-5">
          <p class="text-slate-600 text-lg leading-relaxed">
            Halo! Saya <span class="font-semibold text-slate-800">Habib</span> — seorang Frontend Developer
            yang sedang belajar di <span class="font-semibold text-slate-800">universitas satya terra bhinneka Medan, Indonesia</span>
          </p>
          <p class="text-slate-600 text-lg leading-relaxed">
            Saya percaya bahwa kode yang baik adalah kode yang bisa dibaca manusia, bukan hanya mesin.
            Saya senang bekerja di persimpangan desain dan teknologi — mengubah mockup menjadi
            pengalaman yang terasa hidup.
          </p>
          <p class="text-slate-600 text-lg leading-relaxed">
            dan juga selain belajar codingan saya juga sering mengikuti tournament marching band.
          </p>

          <!-- Journey timeline -->
          <div class="pt-4 space-y-4">
            <div v-for="(item, i) in timeline" :key="i"
              class="flex gap-4 items-start group">
              <div class="flex-shrink-0 w-10 h-10 rounded-full bg-indigo-100 group-hover:bg-indigo-600 transition-colors duration-300 flex items-center justify-center text-indigo-600 group-hover:text-white font-bold text-sm">
                {{ item.year }}
              </div>
              <div class="pt-1.5">
                <p class="font-semibold text-slate-800">{{ item.title }}</p>
                <p class="text-slate-500 text-sm">{{ item.desc }}</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Right: Cards -->
        <div class="md:col-span-2 space-y-4">
          <div v-for="card in cards" :key="card.title"
            class="bg-white rounded-2xl p-6 shadow-sm ring-1 ring-slate-100 hover:ring-indigo-200 hover:shadow-md transition-all duration-300 group">
            <div class="text-3xl mb-3">{{ card.icon }}</div>
            <h3 class="font-bold text-slate-800 mb-1 group-hover:text-indigo-600 transition-colors">{{ card.title }}</h3>
            <p class="text-slate-500 text-sm leading-relaxed">{{ card.desc }}</p>
          </div>

          <a href="#" download
            class="flex items-center justify-center gap-2 w-full bg-indigo-600 text-white py-3.5 rounded-2xl font-semibold hover:bg-indigo-700 transition-colors shadow-lg shadow-indigo-100 mt-4">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 10v6m0 0l-3-3m3 3l3-3m2 8H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"/>
            </svg>
            Download CV
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const timeline = [
  { year: '1', title: 'MOMBC', desc: 'Sebagai juara 2 divisi open class pada tahun 2025' },
  { year: '2', title: 'AMF', desc: 'Sebagai juara 3 divisi open class pada tahun 2025' },
  { year: '3', title: 'SULTAN DELI', desc: 'Sebagai juara 2 divisi logam terbatas pada tahun 2026' },
]

const cards = [
  { icon: '🏫', title: 'SDN 108293 PERBAUNGAN', desc: 'Menempuh pendidikan dari tahun 2014 sampai tahun 2020' },
  { icon: '🏫', title: 'SMP SETIA BUDI ABADI PERBAUNGAN', desc: 'Menempuh pendidikan dari tahun 2020 sampai tahun 2023' },
  { icon: '🏫', title: 'SMK ISTIQLAL DELITUA', desc: 'Menempuh pendidikan dari tahun 2023 sampai tahun 2025  ' },
]
</script>
