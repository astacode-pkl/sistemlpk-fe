<script>
import { ref, onMounted } from 'vue'
import image1 from '@/assets/img/FOTO LAINNYA.jpeg'
import image2 from '@/assets/img/FOTO LAINNYA (13).jpeg'
import image3 from '@/assets/img/FOTO LAINNYA (12).jpeg'
import image4 from '@/assets/img/FOTO LAINNYA (11).jpeg'
import image5 from '@/assets/img/FOTO LAINNYA (10).jpeg'
import image6 from '@/assets/img/FOTO LAINNYA (9).jpeg'
import image7 from '@/assets/img/FOTO LAINNYA (8).jpeg'
import image8 from '@/assets/img/FOTO LAINNYA (7).jpeg'
import image9 from '@/assets/img/FOTO LAINNYA (6).jpeg'
import image10 from '@/assets/img/FOTO LAINNYA (5).jpeg'
import image11 from '@/assets/img/FOTO LAINNYA (4).jpeg'
import image12 from '@/assets/img/FOTO LAINNYA (3).jpeg'
import image13 from '@/assets/img/FOTO LAINNYA (2).jpeg'

export default {
  name: 'Galeri',
  props: {
    previewMode: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      isVisible: false,
      selectedImage: null,
      modalVisible: false,
      loadedImages: new Set(),
      images: [
        {
          id: 1,
          src: image1,
          title: 'Kegiatan LPK Tsukuba'
        },
        {
          id: 2,
          src: image2,
          title: 'Kegiatan LPK Tsukuba'
        },
        {
          id: 3,
          src: image3,
          title: 'Kegiatan LPK Tsukuba'
        },
        {
          id: 4,
          src: image4,
          title: 'Kegiatan LPK Tsukuba'
        },
        {
          id: 5,
          src: image5,
          title: 'Kegiatan LPK Tsukuba'
        },
        {
          id: 6,
          src: image6,
          title: 'Kegiatan LPK Tsukuba'
        },
        {
          id: 7,
          src: image7,
          title: 'Kegiatan LPK Tsukuba'
        },
        {
          id: 8,
          src: image8,
          title: 'Kegiatan LPK Tsukuba'
        },
        {
          id: 9,
          src: image9,
          title: 'Kegiatan LPK Tsukuba'
        },
        {
          id: 10,
          src: image10,
          title: 'Kegiatan LPK Tsukuba'
        },
        {
          id: 11,
          src: image11,
          title: 'Kegiatan LPK Tsukuba'
        },
        {
          id: 12,
          src: image12,
          title: 'Kegiatan LPK Tsukuba'
        },
        {
          id: 13,
          src: image13,
          title: 'Kegiatan LPK Tsukuba'
        }
      ]
    }
  },
  computed: {
    displayedImages() {
      return this.previewMode ? this.images.slice(0, 4) : this.images
    }
  },
  mounted() {
    this.isVisible = true
  },
  methods: {
    onImageLoad(index) {
      this.loadedImages.add(index)
    },
    openModal(image) {
      this.selectedImage = image
      setTimeout(() => {
        this.modalVisible = true
      }, 50)
    },
    closeModal() {
      this.modalVisible = false
      setTimeout(() => {
        this.selectedImage = null
      }, 300)
    }
  }
}
</script>

<template>
  <div class="galeri ">
    <div
      class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 lg:grid-cols-4 gap-4 sm:gap-6 items-center mx-3 sm:mx-5 mt-5 mb-10">
      <div v-for="(image, index) in displayedImages" :key="image.id" data-aos="fade-up"
        class="group relative overflow-hidden rounded-lg shadow-md hover:shadow-xl transition-all duration-300 h-full cursor-pointer"
        :class="{ 'opacity-0 translate-y-4': !isVisible }" @click="openModal(image)">
        <div class="absolute inset-0 bg-gray-200" />
        <div class="w-full h-full">
          <img :src="image.src" :alt="image.title" @load="onImageLoad(index)"
            class="w-full h-64 object-cover transform group-hover:scale-105 transition-transform duration-300" />
        </div>
        <div
          class="absolute inset-0 bg-black/50 opacity-0 group-hover:opacity-100 transition-all duration-300 flex items-center justify-center">
          <h3 class="text-white text-base sm:text-lg md:text-xl font-semibold text-center px-4">{{ image.title }}</h3>
        </div>
      </div>
    </div>



    <!-- Modal -->
    <div v-if="selectedImage"
      class="fixed inset-0 z-[60] overflow-hidden bg-black bg-opacity-80 transition-all duration-300"
      @click="closeModal">
      <div class="flex items-center justify-center min-h-screen p-4">
        <button type="button" class="absolute top-2 right-2 sm:top-3 sm:right-3 z-[70] text-white hover:text-gray-200"
          @click="closeModal">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
          </svg>
        </button>

        <div class="transform transition-all duration-300 max-w-4xl w-full md:w-1/2"
          :class="{ 'opacity-0 scale-95': !modalVisible, 'opacity-100 scale-100': modalVisible }" @click.stop>
          <img :src="selectedImage.src" :alt="selectedImage.title" class="w-full rounded-lg shadow-xl" />
          <h3 class="text-white text-base sm:text-lg md:text-xl font-semibold mt-4 text-center px-2">
            {{ selectedImage.title }}
          </h3>
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
</style>