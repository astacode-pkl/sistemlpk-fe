<template>
  <div>
    <Hero />
    <Visi />
    <div class="max-w-7xl mx-auto">
      <h2 class="text-center text-3xl font-bold text-blue-500 mb-3 animate-fade-in" data-aos="fade-up">Galeri</h2>
      <div class=" mx-auto h-1 w-16 bg-blue-600 rounded mb-4 mt-4 animate-slide-up" data-aos="fade-up"></div>
      <p class="text-center text-gray-600 mb-10 animate-fade-in" data-aos="fade-up">Foto foto kelulusan dan kegiatan</p>
        <Foto />
        <Foto />
        <div class="flex justify-center">
          <nuxt-link to="/galeri">
            <button type="button"
            class="py-3 px-4 inline-flex items-center gap-x-2 text-lg  rounded-2xl border border-transparent bg-blue-600 text-white hover:bg-transparent hover:scale-105 hover:text-blue-600 hover:border hover:border-blue-600  disabled:opacity-50 disabled:pointer-events-none font-semibold hover:transition duration-700">
            Lihat Semua
          </button>
        </nuxt-link>
      </div>
    </div>
    <div class="max-w-7xl mx-auto mt-14">
      <h2 class="text-center text-3xl font-bold text-blue-500 mb-3 animate-fade-in" data-aos="fade-up">Program</h2>
      <div class=" mx-auto h-1 w-16 bg-blue-600 rounded mb-4 mt-4 animate-slide-up" data-aos="fade-up"></div>
      <p class="text-center text-gray-600 mb-10 animate-fade-in" data-aos="fade-up">Program LPK Tsubuka</p>
    <Program />
    </div>
    <div class="max-w-7xl mx-auto mt-14">
      <h2 class="text-center text-3xl font-bold text-blue-500 mb-3 animate-fade-in" data-aos="fade-up">Proses ke jepang</h2>
      <div class=" mx-auto h-1 w-16 bg-blue-600 rounded mb-4 mt-4 animate-slide-up" data-aos="fade-up"></div>
      <p class="text-center text-gray-600 mb-10 animate-fade-in" data-aos="fade-up">Langkah langkah sebelum ke jepang</p>
    <Step />
    </div>
    <Kontak />
  </div>
</template>