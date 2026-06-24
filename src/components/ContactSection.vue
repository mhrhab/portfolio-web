<template>
  <section id="contact" class="py-28 bg-white">
    <div class="max-w-6xl mx-auto px-6">
      <div class="text-center mb-16">
        <p class="text-indigo-600 font-semibold text-sm tracking-widest uppercase mb-3">Kontak</p>
        <h2 class="text-4xl md:text-5xl font-black text-slate-900">Hubungi <span class="text-indigo-600">Saya</span></h2>
      </div>

      <div class="grid md:grid-cols-5 gap-10">
        <!-- Contact info -->
        <div class="md:col-span-2 space-y-6">
          <a v-for="info in contactInfos" :key="info.label"
            :href="info.href"
            class="flex items-center gap-4 p-5 bg-slate-50 rounded-2xl ring-1 ring-slate-100 hover:ring-indigo-200 hover:bg-indigo-50 transition-all duration-300 group">
            <div class="w-12 h-12 bg-white rounded-xl shadow-sm flex items-center justify-center text-xl ring-1 ring-slate-100 group-hover:bg-indigo-600 group-hover:ring-indigo-600 transition-all duration-300">
              <span class="group-hover:brightness-200">{{ info.icon }}</span>
            </div>
            <div>
              <p class="text-xs text-slate-400 uppercase tracking-wide font-medium">{{ info.label }}</p>
              <p class="text-slate-700 font-semibold group-hover:text-indigo-600 transition-colors">{{ info.value }}</p>
            </div>
          </a>

          <!-- Social links -->
          <div class="flex gap-3 pt-2">
            <a v-for="social in socials" :key="social.label"
              :href="social.href" target="_blank"
              class="w-11 h-11 bg-slate-100 rounded-xl flex items-center justify-center text-slate-500 hover:bg-indigo-600 hover:text-white transition-all duration-200 hover:-translate-y-0.5"
              :title="social.label">
              <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                <path :d="social.icon"/>
              </svg>
            </a>
          </div>
        </div>

        <!-- Contact form -->
        <div class="md:col-span-3">
          <div class="bg-slate-50 rounded-3xl p-8 ring-1 ring-slate-100">
            <div v-if="submitted" class="text-center py-10">
              <div class="text-6xl mb-4">🎉</div>
              <h3 class="text-xl font-bold text-slate-800 mb-2">Pesan Terkirim!</h3>
              <p class="text-slate-500">Terima kasih sudah menghubungi saya. Saya akan segera membalas.</p>
              <button @click="submitted = false" class="mt-6 text-indigo-600 font-semibold text-sm hover:underline">
                Kirim pesan lain
              </button>
            </div>

            <div v-else class="space-y-5">
              <div class="grid sm:grid-cols-2 gap-5">
                <div>
                  <label class="block text-sm font-semibold text-slate-600 mb-2">Nama</label>
                  <input v-model="form.name" type="text" placeholder="Nama kamu"
                    class="w-full bg-white border border-slate-200 rounded-xl px-4 py-3 text-slate-800 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-400 focus:border-transparent transition-all placeholder-slate-300"/>
                </div>
                <div>
                  <label class="block text-sm font-semibold text-slate-600 mb-2">Email</label>
                  <input v-model="form.email" type="email" placeholder="email@kamu.com"
                    class="w-full bg-white border border-slate-200 rounded-xl px-4 py-3 text-slate-800 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-400 focus:border-transparent transition-all placeholder-slate-300"/>
                </div>
              </div>

              <div>
                <label class="block text-sm font-semibold text-slate-600 mb-2">Subjek</label>
                <input v-model="form.subject" type="text" placeholder="Perihal pesan kamu"
                  class="w-full bg-white border border-slate-200 rounded-xl px-4 py-3 text-slate-800 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-400 focus:border-transparent transition-all placeholder-slate-300"/>
              </div>

              <div>
                <label class="block text-sm font-semibold text-slate-600 mb-2">Pesan</label>
                <textarea v-model="form.message" rows="5" placeholder="Ceritakan proyekmu..."
                  class="w-full bg-white border border-slate-200 rounded-xl px-4 py-3 text-slate-800 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-400 focus:border-transparent transition-all placeholder-slate-300 resize-none"></textarea>
              </div>

              <button @click="handleSubmit"
                :disabled="sending"
                class="w-full bg-indigo-600 text-white py-4 rounded-xl font-bold hover:bg-indigo-700 transition-all duration-200 hover:-translate-y-0.5 shadow-lg shadow-indigo-200 disabled:opacity-70 disabled:cursor-not-allowed flex items-center justify-center gap-2">
                <span v-if="sending">Mengirim...</span>
                <span v-else>Kirim Pesan 🚀</span>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive } from 'vue'

const submitted = ref(false)
const sending = ref(false)

const form = reactive({ name: '', email: '', subject: '', message: '' })

const handleSubmit = async () => {
  if (!form.name || !form.email || !form.message) return
  sending.value = true
  await new Promise(r => setTimeout(r, 1500))
  sending.value = false
  submitted.value = true
}

const contactInfos = [
  { icon: '✉️', label: 'Email', value: 'habib@email.com', href: 'mailto:habib@email.com' },
  { icon: '📍', label: 'Lokasi', value: 'Medan, Indonesia', href: '#' },
  { icon: '💼', label: 'Status', value: 'Mahasiswa', href: '#' },
]
</script>
