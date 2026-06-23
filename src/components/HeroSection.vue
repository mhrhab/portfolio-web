<template>
  <section
    id="hero"
    class="min-h-screen bg-white flex items-center pt-20 relative overflow-hidden"
  >
    <!-- Background -->
    <div
      class="absolute inset-0 bg-[linear-gradient(to_right,#f1f5f9_1px,transparent_1px),linear-gradient(to_bottom,#f1f5f9_1px,transparent_1px)] bg-[size:4rem_4rem] opacity-60"
    ></div>

    <div
      class="absolute top-20 right-0 w-[500px] h-[500px] bg-indigo-50 rounded-full -translate-y-1/4 translate-x-1/4 blur-3xl opacity-70"
    ></div>

    <div
      class="max-w-6xl mx-auto px-6 py-20 grid md:grid-cols-2 gap-16 items-center relative z-10"
    >
      <!-- Text -->
      <div class="order-2 md:order-1">
        <p class="text-indigo-600 font-semibold text-sm tracking-widest">
          Haii!
        </p>

        <h1
          class="text-5xl md:text-6xl font-black text-slate-900 leading-tight mb-2"
        >
          Saya <span class="text-indigo-600">M.HABIB</span>
        </h1>

        <div
          class="text-3xl md:text-4xl font-bold text-slate-700 mb-6 h-12 flex items-center"
        >
          <span class="typewriter-container">
            <span ref="typewriterEl" class="typewriter-text"></span>
            <span class="typewriter-cursor text-indigo-600">|</span>
          </span>
        </div>

        <p class="text-slate-500 text-lg leading-relaxed mb-10 max-w-md">
          Saya Adalah Seorang Mahasiswa semester 2 yang sedang belajar di Universitas Satya Terra Bhinneka
          Dengan Jurusan Informatika.</p>

        <div class="flex flex-wrap gap-4">
          <a
            href="#contact"
            class="bg-indigo-600 text-white px-8 py-3.5 rounded-full font-semibold hover:bg-indigo-700 transition-all duration-200 hover:-translate-y-0.5 shadow-lg shadow-indigo-200"
          >
            Hubungi Saya
          </a>
        </div>

      </div>

      <!-- Avatar -->
      <div class="order-1 md:order-2 flex justify-center md:justify-end">
        <div class="relative">
          <div
            class="w-72 h-72 md:w-80 md:h-80 rounded-3xl overflow-hidden shadow-2xl shadow-indigo-100 ring-1 ring-indigo-100"
          >
            <img
              :src="fotoProfile"
              alt="Foto Profile"
              class="w-full h-full object-cover"
            />
          </div>

          <!-- Floating Tags -->
          <div
            class="absolute -top-4 -left-4 bg-white rounded-2xl shadow-lg px-4 py-2 flex items-center gap-2 text-sm font-semibold text-slate-700"
          >
            ⚡ Vue.js
          </div>

          <div
            class="absolute -bottom-4 -right-4 bg-white rounded-2xl shadow-lg px-4 py-2 flex items-center gap-2 text-sm font-semibold text-slate-700"
          >
            🎨 Tailwind CSS
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";
import fotoProfile from "../assets/fotoprofile.jpg";

const typewriterEl = ref(null);

const phrases = [
  "Frontend Developer.",
  "UI Designer."
];



let phraseIndex = 0;
let charIndex = 0;
let isDeleting = false;

const type = () => {
  if (!typewriterEl.value) return;

  const current = phrases[phraseIndex];

  if (isDeleting) {
    typewriterEl.value.textContent = current.substring(
      0,
      charIndex - 1
    );
    charIndex--;
  } else {
    typewriterEl.value.textContent = current.substring(
      0,
      charIndex + 1
    );
    charIndex++;
  }

  let speed = isDeleting ? 60 : 100;

  if (!isDeleting && charIndex === current.length) {
    speed = 1800;
    isDeleting = true;
  } else if (isDeleting && charIndex === 0) {
    isDeleting = false;
    phraseIndex = (phraseIndex + 1) % phrases.length;
    speed = 400;
  }

  setTimeout(type, speed);
};

onMounted(() => {
  setTimeout(type, 600);
});
</script>

<style scoped>
.typewriter-cursor {
  animation: blink 0.75s step-end infinite;
}

@keyframes blink {
  from,
  to {
    opacity: 1;
  }

  50% {
    opacity: 0;
  }
}
</style>