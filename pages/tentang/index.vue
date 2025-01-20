<template>
    <div class="min-h-screen">
      <!-- Hero Section -->
      <div class="h-[25vh] w-full relative mt-20 mb-10 shadow-md flex items-center justify-center">
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
          <img src="assets/img/bg-tentang.webp" alt="foto-bg"
            class="w-full h-full object-cover absolute inset-0" />
          <div class="absolute inset-0 bg-black opacity-60" />
          <div
            class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 flex flex-col items-center gap-2">
            <h1 class="text-white text-4xl font-semibold z-10  text-center" data-aos="fade-right">
              Tentang
            </h1>
            <h4
            class="text-white text-base sm:text-lg font-semibold z-10 opacity-0 translate-x-full animate-[slideInRight_0.5s_ease-out_0.2s_forwards] text-center">
            <nuxt-link to="/" class="text-white hover:text-blue-100">Home</nuxt-link> >
            <nuxt-link to="/tentang" class="text-blue-400 ">Tentang</nuxt-link>
          </h4>
          </div>
        </div>
      </div>
    </div>
  
      <!-- History Section -->
      <div 
        v-observe-visibility="(isVisible) => visibilityChanged('history', isVisible)"
        class="max-w-6xl mx-auto px-4"
      >
        <h3 
          :class="[
            'text-xl md:text-2xl font-bold text-blue-600 mb-6 text-center transition-all duration-700',
            isVisible.history ? 'animate-slideDown opacity-100' : 'opacity-0 -translate-y-10'
          ]"
        >
          Sejarah LPK Tsukuba Indonesia
        </h3>
        
        <div 
          :class="[
            'bg-gray-50 rounded-lg shadow-md overflow-hidden mb-12 transition-all duration-700 delay-300',
            isVisible.history ? 'animate-slideUp opacity-100' : 'opacity-0 translate-y-10'
          ]"
        >
          <div class="p-4 md:p-8">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-6 md:gap-12">
              <div class="space-y-4 md:space-y-6 text-base md:text-lg text-center lg:text-left">
                <p class="text-gray-600 leading-relaxed">
                  LPK Tsukuba Indonesia didirikan pada bulan Agustus 2024 di Ciawi, Kabupaten Tasikmalaya, Jawa Barat Indonesia. LPK Tsukuba Indonesia adalah lembaga pendidikan bahasa Jepang untuk Program Pemagang ke Jepang, dan telah mendapatkan izin resmi dari pemerintah Indonesia.
                </p>
                <p class="text-gray-600 leading-relaxed">
                  LPK Tsukuba Indonesia membuka kelas pendidikan Bahasa Jepang yang berorientasi memberikan pembekalan sikap, mental, serta bahasa dan budaya Jepang bagi calon peserta magang, dan melatih calon peserta magang agar menjadi pemagang yang andal dan sesuai dengan kompetensi yang dibutuhkan oleh perusahaan Jepang.
                </p>
              </div>
              <div class="order-first lg:order-last">
                <div class="relative h-64 lg:h-full w-full rounded-lg overflow-hidden">
                  <img
                    src="assets/img/hero.jpg"
                    alt="LPK TSUKUBA INDONESIA"
                    class="absolute inset-0 w-full h-full object-cover transition-transform duration-300 ease-in-out transform hover:scale-110"
                  />
                  <div class="absolute inset-0 bg-black bg-opacity-40 flex flex-col justify-center items-center p-6">
                    <h4 class="text-white text-xl font-bold mb-2 text-center">LPK TSUKUBA INDONESIA</h4>
                    <p class="text-white text-sm text-center">職業訓練機関つくばインドネシア</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
  
        <!-- Separator Line -->
        <div class="w-1/2 h-px bg-gray-300 mx-auto mb-12"></div>
  
        <!-- Curriculum Section -->
        <div 
          v-observe-visibility="(isVisible) => visibilityChanged('curriculum', isVisible)"
          class="max-w-5xl mx-auto"
        >
          <div class="text-center mb-8">
            <h2 
              :class="[
                'text-2xl md:text-3xl font-bold text-blue-600 relative inline-block transition-all duration-700',
                isVisible.curriculum ? 'animate-slideDown opacity-100' : 'opacity-0 -translate-y-10'
              ]"
            >
              Kurikulum Dan Metode Pengajaran
            </h2>
          </div>
  
          <div 
            :class="[
              'text-center mb-8 md:mb-16 transition-all duration-700 delay-300',
              isVisible.curriculum ? 'animate-slideUp opacity-100' : 'opacity-0 translate-y-10'
            ]"
          >
            <p class="text-base md:text-lg text-gray-600 max-w-3xl mx-auto">
              Sebagai acuan untuk dapat mengikuti keinginan dan harapan dari LPK SO kami menggunakan modul sebagai berikut:
            </p>
          </div>
  
          <div data-aos="fade-up" data-aos-duration="2500" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4 md:gap-6 px-4">
            <div 
              v-for="(item, index) in curriculumItems" 
              :key="index" 
              class="group"
              :class="[
                'transition-all duration-700',
                isVisible.curriculum ? 'animate-slideUp opacity-100' : 'opacity-0 translate-y-10'
              ]"
              :style="{ transitionDelay: (400 + (index * 100)) + 'ms' }"
            >
              <div class="bg-gray-50 rounded-2xl shadow-lg p-4 md:p-5 transform transition-all duration-300 hover:-translate-y-2 hover:shadow-xl">
                <div class="flex flex-col items-center space-y-4">
                  <div class="w-12 md:w-16 h-12 md:h-16 bg-blue-100 rounded-lg flex items-center justify-center group-hover:bg-blue-200 transition-colors duration-300">
                    <svg xmlns="http://www.w3.org/2000/svg" class="w-6 md:w-8 h-6 md:h-8 text-blue-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" :d="item.icon" />
                    </svg>
                  </div>
                  <h3 class="text-lg md:text-xl font-semibold text-gray-900 text-center">{{ item.title }}</h3>
                  <div class="opacity-0 group-hover:opacity-100 transition-opacity duration-300">
                    <p class="text-sm text-gray-600 text-center">
                      {{ item.description }}
                    </p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
  
        <!-- Separator Line -->
        <div class="w-1/2 h-px bg-gray-300 mx-auto my-12"></div>
  
        <!-- Licensing Section -->
        <div 
          v-observe-visibility="(isVisible) => visibilityChanged('licensing', isVisible)"
          class="mt-12 md:mt-16 mb-16 md:mb-20"
        >
          <div class="text-center mb-8">
            <h2 
              :class="[
                'text-2xl md:text-3xl font-bold text-blue-600 transition-all duration-700',
                isVisible.licensing ? 'animate-slideDown opacity-100' : 'opacity-0 -translate-y-10'
              ]"
            >
              Perizinan
              <div class="mt-2 mx-auto h-1 w-16 bg-blue-600 rounded"></div>
            </h2>
          </div>
          
          <div 
            :class="[
              'bg-gradient-to-r from-blue-50 to-blue-100 rounded-lg p-4 md:p-8 lg:p-12 shadow-lg max-w-4xl mx-auto transition-all duration-700 delay-300',
              isVisible.licensing ? 'animate-slideUp opacity-100 hover:shadow-2xl hover:scale-105' : 'opacity-0 translate-y-10'
            ]"
          >
            <p class="text-base md:text-xl font-semibold text-gray-700 text-center mb-4">
              Sertifikat Standar: <span class="font-bold text-blue-600">14082400621380001</span>
            </p>
            <p class="text-base md:text-xl text-gray-700 text-center">
              Akta Notaris: <span class="font-bold text-blue-600">Mohamad Hikmat, S.H.</span> Nomor 12 Tanggal 26 Juli 2024
            </p>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'AboutPage',
    data() {
      return {
        loading: true,
        isVisible: {
          tentang: false,
          history: false,
          curriculum: false,
          licensing: false
        },
        curriculumItems: [
          {
            title: "Minna No Nihongo I dan II",
            description: "Pembelajaran dasar bahasa Jepang yang sistematis",
            icon: "M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
          },
          {
            title: "Irodori",
            description: "Pembelajaran praktis untuk kehidupan di Jepang",
            icon: "M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10"
          },
          {
            title: "Marugoto",
            description: "Pembelajaran secara aktif & dinamis mencakup informasi budaya Jepang",
            icon: "M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10"
          }
        ]
      }
    },
    mounted() {
      setTimeout(() => {
        this.loading = false;
        this.isVisible.tentang = true;
      }, 1000);
    },
    methods: {
      visibilityChanged(section, isVisible) {
        if (section === 'history' && isVisible) {
          setTimeout(() => {
            this.isVisible[section] = isVisible;
          }, 1000); 
        } else {
          this.isVisible[section] = isVisible;
        }
      }
    },
    directives: {
      observeVisibility: {
        mounted(el, binding) {
          const observer = new IntersectionObserver((entries) => {
            binding.value(entries[0].isIntersecting)
          }, {
            threshold: 0.1, 
            rootMargin: '0px'
          })
          observer.observe(el)
          el._observer = observer
        },
        unmounted(el) {
          if (el._observer) {
            el._observer.disconnect()
          }
        }
      }
    }
  }
  </script>
  
  <style>
  @keyframes slideDown {
    0% {
      opacity: 0;
      transform: translateY(-30px);
    }
    100% {
      opacity: 1;
      transform: translateY(0);
    }
  }
  
  @keyframes slideUp {
    0% {
      opacity: 0;
      transform: translateY(30px);
    }
    100% {
      opacity: 1;
      transform: translateY(0);
    }
  }
  
  .animate-slideDown {
    animation: slideDown 0.7s ease-out forwards;
  }
  
  .animate-slideUp {
    animation: slideUp 0.7s ease-out forwards;
  }
  
  .delay-300 {
    animation-delay: 300ms;
  }
  
  .transition-all {
    transition-property: all;
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  }
  
  .duration-700 {
    transition-duration: 700ms;
  }
  
  .hover\:scale-105:hover {
    transform: scale(1.05);
  }
  
  .hover\:shadow-xl:hover {
    box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
  }
  
  * {
    backface-visibility: hidden;
    -webkit-font-smoothing: antialiased;
  }
  
  @media (max-width: 640px) {
    .animate-slideUp, .animate-slideDown {
      animation-duration: 0.5s;
    }
  }
  </style>