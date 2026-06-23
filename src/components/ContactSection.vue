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

const socials = [
  {
    label: 'GitHub',
    href: '#',
    icon: 'M12 2C6.477 2 2 6.477 2 12c0 4.418 2.865 8.166 6.839 9.489.5.092.682-.217.682-.482 0-.237-.008-.866-.013-1.7-2.782.603-3.369-1.342-3.369-1.342-.454-1.155-1.11-1.462-1.11-1.462-.908-.62.069-.608.069-.608 1.003.07 1.531 1.03 1.531 1.03.892 1.529 2.341 1.087 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.11-4.555-4.943 0-1.091.39-1.984 1.029-2.683-.103-.253-.446-1.27.098-2.647 0 0 .84-.269 2.75 1.025A9.578 9.578 0 0112 6.836c.85.004 1.705.115 2.504.337 1.909-1.294 2.747-1.025 2.747-1.025.546 1.377.202 2.394.1 2.647.64.699 1.028 1.592 1.028 2.683 0 3.842-2.339 4.687-4.566 4.935.359.309.678.919.678 1.852 0 1.336-.012 2.415-.012 2.743 0 .267.18.578.688.48C19.138 20.163 22 16.418 22 12c0-5.523-4.477-10-10-10z'
  },
  {
    label: 'LinkedIn',
    href: '#',
    icon: 'M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z'
  },
  {
    label: 'Twitter/X',
    href: '#',
    icon: 'M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z'
  },
]
</script>
