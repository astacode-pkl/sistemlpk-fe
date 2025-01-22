<script setup>
useHead({
  title: 'Galeri',
  meta: [
    {
      name: 'description',
      content: 'Galeri Page'
    }
  ]
})

import { ref, onMounted } from 'vue'

const loading = ref(true)

onMounted(() => {
  setTimeout(() => {
    loading.value = false
  }, 2000)
})
</script>

<template>
  <div class="galeri">
    <div class="h-[30vh] w-full relative mb-10 shadow-md flex items-center justify-center">
      <div>
        <div v-if="loading">
          <div v-for="n in skeletonCount" :key="n"
            class="bg-gray-500 border-2 border-gray-100 rounded-md mb-4 p-4 flex items-center">
            <div class="w-12 h-12 bg-gray-300 rounded-full mr-4"></div>
            <div class="flex-1">
              <div class="w-3/4 h-4 bg-gray-300 rounded-md mb-2"></div>
              <div class="w-1/2 h-3 bg-gray-300 rounded-md"></div>
            </div>
          </div>
        </div>

        <div v-else>

          <img src="assets/img/hero.jpg" alt="foto-persyaratan1" class="w-full h-full object-cover absolute inset-0" />
          <div class="absolute inset-0 bg-black opacity-60" />
          <div
            class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 flex flex-col items-center gap-2">
            <h1 class="text-white text-4xl font-semibold z-10  text-center" data-aos="fade-right">
              Galeri
            </h1>
            <h4
              class="text-white text-base sm:text-lg font-semibold z-10 opacity-0 translate-x-full animate-[slideInRight_0.5s_ease-out_0.2s_forwards] text-center">
              <nuxt-link to="/" class="text-white hover:text-blue-100">Home</nuxt-link> >
              <nuxt-link to="/galeri" class="text-blue-400 ">Galeri</nuxt-link>
            </h4>
          </div>
        </div>
      </div>
    </div>


    <h3 class="text-center text-xl text-blue-600 font-semibold mb-10 animate-fade-in" data-aos="fade-up">Foto Kelulusan
    </h3>
    <Foto />
    <h3 class="text-center  text-xl text-blue-600 font-semibold  mb-10 animate-fade-in" data-aos="fade-up">Foto Kegiatan
      Lainnya</h3>
    <Galeri :preview-mode="false" />

  </div>
</template>

<style>
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(1rem);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideInLeft {
  from {
    opacity: 0;
    transform: translateX(-100%);
  }

  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slideInRight {
  from {
    opacity: 0;
    transform: translateX(100%);
  }

  to {
    opacity: 1;
    transform: translateX(0);
  }
}
</style>