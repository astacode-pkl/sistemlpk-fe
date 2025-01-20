<template>
  <!-- galeri -->
  <div class="galeri my-14 mx-8">
    <h3 class="text-xl text-center mb-5 font-bold text-blue-600" data-aos="fade-up">
      Galeri
    </h3>
    <h4 class="font-semibold text-lg text-gray-800 text-center" data-aos="fade-up">Kelulusan dan Keberangkatan</h4>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 p-10">
      <img src="/assets/img/1.png" alt="foto kelulusan" class="rounded-lg" data-aos="fade-up">
      <img src="/assets/img/2.png" alt="foto kelulusan" class="rounded-lg" data-aos="fade-up" data-aos-delay="200">
      <img src="/assets/img/3.png" alt="foto kelulusan" class="rounded-lg" data-aos="fade-up" data-aos-delay="400">
    </div>
    <h4 class="font-semibold text-lg text-gray-800 text-center" data-aos="fade-up">Foto Kegiatan</h4>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 p-10">
      <img src="/assets/img/1.png" alt="foto kelulusan" class="rounded-lg" data-aos="fade-up">
      <img src="/assets/img/2.png" alt="foto kelulusan" class="rounded-lg" data-aos="fade-up" data-aos-delay="200">
      <img src="/assets/img/3.png" alt="foto kelulusan" class="rounded-lg" data-aos="fade-up" data-aos-delay="400">
    </div>
    <div class="flex justify-center">
      <nuxt-link to="/galeri">
        <button type="button"
          class="py-3 px-4 inline-flex items-center gap-x-2 text-lg  rounded-2xl border border-transparent bg-blue-600 text-white hover:bg-transparent hover:scale-105 hover:text-blue-600 hover:border hover:border-blue-600  disabled:opacity-50 disabled:pointer-events-none font-semibold hover:transition duration-700">
          Lihat Semua
        </button>
      </nuxt-link>
    </div>
  </div>
  <!-- end galeri -->
</template>

