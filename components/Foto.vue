<script>
// Script section tetap sama
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
      isDragging: false,
      startPos: 0,
      currentTranslate: 0,
      prevTranslate: 0,
      currentIndex: 0,
      images: [
        {
          id: 1,
          src: image1,
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
        },
        {
          id: 4,
          src: image3,
          title: 'Kelulusan Ezy De Apri Faizal'
        },
        {
          id: 5,
          src: image3,
          title: 'Kelulusan Ezy De Apri Faizal'
        },
        {
          id: 6,
          src: image3,
          title: 'Kelulusan Ezy De Apri Faizal'
        },
        {
          id: 7,
          src: image3,
          title: 'Kelulusan Ezy De Apri Faizal'
        },
        {
          id: 8,
          src: image3,
          title: 'Kelulusan Ezy De Apri Faizal'
        },
        {
          id: 9,
          src: image3,
          title: 'Kelulusan Ezy De Apri Faizal'
        },
        {
          id: 10,
          src: image3,
          title: 'Kelulusan Ezy De Apri Faizal'
        },
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
      this.currentIndex = this.images.findIndex(img => img.id === image.id);
      setTimeout(() => {
        this.modalVisible = true;
      }, 50);
    },
    closeModal() {
      this.modalVisible = false;
      setTimeout(() => {
        this.selectedImage = null;
      }, 300);
    },
    touchStart(e) {
      this.isDragging = true;
      this.startPos = e.type === 'mousedown' ? e.clientX : e.touches[0].clientX;
      const slider = this.$refs.slider;
      slider.style.transition = 'none';
    },
    touchMove(e) {
      if (!this.isDragging) return;
      const currentPosition = e.type === 'mousemove' ? e.clientX : e.touches[0].clientX;
      const diff = currentPosition - this.startPos;
      const slider = this.$refs.slider;
      const maxTranslate = -(slider.scrollWidth - slider.offsetWidth);

      this.currentTranslate = Math.max(Math.min(this.prevTranslate + diff, 0), maxTranslate);
      this.updateSliderPosition();
    },
    touchEnd() {
      this.isDragging = false;
      this.prevTranslate = this.currentTranslate;
      const slider = this.$refs.slider;
      slider.style.transition = 'transform 0.3s ease';
    },
    updateSliderPosition() {
      const slider = this.$refs.slider;
      if (slider) {
        slider.style.transform = `translateX(${this.currentTranslate}px)`;
      }
    },
    scrollPrev() {
      const slider = this.$refs.slider;
      const itemWidth = slider.offsetWidth;
      this.currentTranslate = Math.min(this.currentTranslate + itemWidth, 0);
      this.prevTranslate = this.currentTranslate;
      slider.style.transition = 'transform 0.3s ease';
      this.updateSliderPosition();
    },
    scrollNext() {
      const slider = this.$refs.slider;
      const itemWidth = slider.offsetWidth;
      const maxTranslate = -(slider.scrollWidth - slider.offsetWidth);
      this.currentTranslate = Math.max(this.currentTranslate - itemWidth, maxTranslate);
      this.prevTranslate = this.currentTranslate;
      slider.style.transition = 'transform 0.3s ease';
      this.updateSliderPosition();
    }
  }
}

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

    <div class="relative px-5  mt-5 mb-10">
      <!-- Prev Button -->
      <button @click="scrollPrev"
        class="absolute left-2 sm:left-4 md:left-6 lg:left-8 top-1/2 -translate-y-1/2 z-10 bg-white/80 hover:bg-white shadow-md rounded-full p-2 sm:p-3 transition-all duration-300">
        <svg class="w-5 h-5 sm:w-6 sm:h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
        </svg>
      </button>

      <!-- Next Button -->
      <button @click="scrollNext"
        class="absolute right-2 sm:right-4 md:right-6 lg:right-8 top-1/2 -translate-y-1/2 z-10 bg-white/80 hover:bg-white shadow-md rounded-full p-2 sm:p-3 transition-all duration-300">
        <svg class="w-5 h-5 sm:w-6 sm:h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
        </svg>
      </button>

      <div class="overflow-hidden rounded-md">
        <div ref="slider" class="flex gap-4 sm:gap-6 cursor-grab active:cursor-grabbing" @mousedown="touchStart"
          @mousemove="touchMove" @mouseup="touchEnd" @mouseleave="touchEnd" @touchstart="touchStart"
          @touchmove="touchMove" @touchend="touchEnd">
          <div v-for="(image, index) in images" :key="image.id"
            class="flex-shrink-0 w-[100%] sm:w-[100%] md:w-[30.5%] lg:w-[23.5%]">
            <div
              class="group relative overflow-hidden rounded-lg shadow-md hover:shadow-xl transition-all duration-300 h-full cursor-pointer"
              :class="{ 'opacity-0 translate-y-4': !isVisible }" @click="openModal(image)">
              <div class="absolute inset-0 bg-gray-200 animate-pulse" />
              <div class="w-full h-full">
                <img :src="image.src" :alt="image.title" @load="onImageLoad(index)"
                  class="w-full h-auto transform group-hover:scale-105 transition-transform duration-300" />
              </div>
              <div
                class="absolute inset-0 bg-black/50 opacity-0 group-hover:opacity-100 transition-all duration-300 flex items-center justify-center">
                <h3 class="text-white text-base sm:text-lg md:text-xl font-semibold text-center px-4">{{ image.title }}
                </h3>
              </div>
            </div>
          </div>
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