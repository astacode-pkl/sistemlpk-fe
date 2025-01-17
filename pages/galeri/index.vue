<script>
import image1 from '@/assets/img/1.png'
import image2 from '@/assets/img/2.png'
import image3 from '@/assets/img/3.png'
export default {
  name: 'GalleryGrid',
  data() {
    return {
      isVisible: false,
      selectedImage: null,
      modalVisible: false,
      loadedImages: new Set(),
      images: [
        {
          id: 1,
          src:  image1,
          title: 'Kelulusan Aril Rianto'
        },
        {
          id: 2,
          src: image2,
          title: 'Kelulusan Abi Yusuf Latif Abdilah'
        },
        {
          id: 3,
          src: image3,
          title: 'Kelulusan Ezy De Apri Faizal'
        }
      ]
    }
  },
  mounted() {
    this.isVisible = true;
  },
  methods: {
    onImageLoad(index) {
      this.loadedImages.add(index);
    },
    openModal(image) {
      this.selectedImage = image;
      setTimeout(() => {
        this.modalVisible = true;
      }, 50);
    },
    closeModal() {
      this.modalVisible = false;
      setTimeout(() => {
        this.selectedImage = null;
      }, 300);
    }
  }
}

import { ref, onMounted } from 'vue'

const loading = ref(true)

onMounted(() => {
  setTimeout(() => {
    loading.value = false
  },2000)
})
</script>

<template>
  <div class="galeri">
    <div v-if="loading">
      <div
        v-for="n in skeletonCount"
        :key="n"
        class="bg-gray-500 border-2 border-gray-100 rounded-md mb-4 p-4 flex items-center"
      >
        <div class="w-12 h-12 bg-gray-300 rounded-full mr-4"></div>
        <div class="flex-1">
          <div class="w-3/4 h-4 bg-gray-300 rounded-md mb-2"></div>
          <div class="w-1/2 h-3 bg-gray-300 rounded-md"></div>
        </div>
      </div>
    </div>
    <div v-else>
      <div class="h-[25vh] sm:h-[30vh] md:h-[35vh] w-full relative mt-20 mb-10 shadow-md flex items-center justify-center overflow-hidden">
        <img
          src="assets/img/hero.jpg"
          alt="foto-persyaratan1"
          class="w-full h-full object-cover absolute inset-0"
        />
        <div class="absolute inset-0 bg-black opacity-40" />
        <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 flex flex-col items-center gap-2 w-full px-4">
          <!-- Animate main title from left -->
          <h1 
            class="text-white text-2xl sm:text-3xl md:text-4xl font-semibold z-10 opacity-0 -translate-x-full animate-[slideInLeft_0.5s_ease-out_forwards] text-center"
          >
            Galeri
          </h1>
          <!-- Animate subtitle from right with delay -->
          <h1 
            class="text-white text-base sm:text-lg font-semibold z-10 opacity-0 translate-x-full animate-[slideInRight_0.5s_ease-out_0.2s_forwards] text-center"
          >
            Kelulusan dan Keberangkatan
          </h1>
        </div>
      </div>
    </div>
    
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4 sm:gap-6 items-center mx-3 sm:mx-5 mt-5 mb-3">
      <div v-for="(image, index) in images" :key="image.id"
           class="group relative overflow-hidden rounded-lg shadow-md hover:shadow-xl transition-all duration-300"
           :class="{'opacity-0 translate-y-4': !isVisible}"
           :style="{ animation: `fadeInUp 0.6s ease forwards ${index * 0.2}s` }"
           @click="openModal(image)">
        <!-- Placeholder saat loading -->
        <div class="absolute inset-0 bg-gray-200 animate-pulse" />
        
        <img 
          :src="image.src" 
          :alt="image.title"
          @load="onImageLoad(index)"
          class="w-full sm:h-56 md:h-64 object-cover transform group-hover:scale-105 transition-transform duration-300" 
        />
        <div class="absolute inset-0 bg-black/50 opacity-0 group-hover:opacity-100 transition-all duration-300 flex items-center justify-center">
          <h3 class="text-white text-base sm:text-lg md:text-xl font-semibold text-center px-4">{{ image.title }}</h3>
        </div>
      </div>
    </div>

    <!-- Modal -->
    <div v-if="selectedImage" 
         class="fixed inset-0 z-[60] overflow-hidden bg-black bg-opacity-80 transition-all duration-300"
         @click="closeModal">
      <div class="flex items-center justify-center min-h-screen p-4">
        <!-- Modal Close Button -->
        <button type="button" 
                class="absolute top-2 right-2 sm:top-3 sm:right-3 z-[70] text-white hover:text-gray-200"
                @click="closeModal">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
          </svg>
        </button>

        <!-- Modal Content -->
        <div class="transform transition-all duration-300 max-w-4xl w-full"
             :class="{'opacity-0 scale-95': !modalVisible, 'opacity-100 scale-100': modalVisible}"
             @click.stop>
          <img :src="selectedImage.src" 
               :alt="selectedImage.title" 
               class="w-full rounded-lg shadow-xl" />
          <h3 class="text-white text-base sm:text-lg md:text-xl font-semibold mt-4 text-center px-2">{{ selectedImage.title }}</h3>
        </div>
      </div>
    </div>
   
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