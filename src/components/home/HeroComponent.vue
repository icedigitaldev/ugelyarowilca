<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const currentIndex = ref(0);
const totalItems = 3;
const intervalTime = 5000;
let autoplayInterval = null;
const isAnimating = ref(false);

const goToNext = () => {
  if (isAnimating.value) return;
  isAnimating.value = true;
  currentIndex.value = (currentIndex.value + 1) % totalItems;
  setTimeout(() => {
    isAnimating.value = false;
  }, 800);
};

const goToPrev = () => {
  if (isAnimating.value) return;
  isAnimating.value = true;
  currentIndex.value = (currentIndex.value - 1 + totalItems) % totalItems;
  setTimeout(() => {
    isAnimating.value = false;
  }, 800);
};

const startAutoplay = () => {
  stopAutoplay();
  autoplayInterval = setInterval(goToNext, intervalTime);
};

const stopAutoplay = () => {
  if (autoplayInterval) {
    clearInterval(autoplayInterval);
    autoplayInterval = null;
  }
};

const handleUserInteraction = () => {
  stopAutoplay();
  setTimeout(startAutoplay, 5000);
};

onMounted(() => {
  startAutoplay();
});

onUnmounted(() => {
  stopAutoplay();
});
</script>

<template>
  <div class="mt-18">
    <div id="controls-carousel" class="relative w-full h-full bg-[#1F2B6C]" data-carousel="static">
      <!-- Carousel wrapper -->
      <div class="relative overflow-hidden h-[250px] md:h-[650px]">
        <transition-group name="fade">
          <!-- Item 1 -->
          <div
              v-if="currentIndex === 0"
              key="slide-0"
              class="carousel-item h-full"
          >
            <img
                src="@/assets/img/hero1.png"
                class=" w-full object-cover object-center"
                alt="Image 1"
            />
          </div>
          <!-- Item 2 -->
          <div
              v-if="currentIndex === 1"
              key="slide-1"
              class="carousel-item h-full"
          >
            <img
                src="@/assets/img/hero2.png"
                class="w-full object-cover object-center"
                alt="Image 2"
            />
          </div>
          <!-- Item 3 -->
          <div
              v-if="currentIndex === 2"
              key="slide-2"
              class="carousel-item h-full"
          >
            <img
                src="@/assets/img/hero3.png"
                class="w-full object-cover object-center"
                alt="Image 3"
            />
          </div>
        </transition-group>
      </div>
      <!-- Slider controls -->
      <button
          type="button"
          class="absolute top-0 start-0 z-30 flex items-center justify-center h-full px-4 cursor-pointer group focus:outline-none"
          @click="goToPrev(); handleUserInteraction();"
          :disabled="isAnimating"
      >
      <span class="inline-flex items-center justify-center w-10 h-10 rounded-full bg-white/20 group-hover:bg-white/50  group-focus:ring-4 group-focus:ring-white group-focus:outline-none">
        <svg
            class="w-4 h-4 text-white dark:text-gray-800 rtl:rotate-180"
            aria-hidden="true"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 6 10"
        >
          <path
              stroke="white"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M5 1 1 5l4 4"
          />
        </svg>
        <span class="sr-only">Previous</span>
      </span>
      </button>

      <button
          type="button"
          class="absolute top-0 end-0 z-30 flex items-center justify-center h-full px-4 cursor-pointer group focus:outline-none"
          @click="goToNext(); handleUserInteraction();"
          :disabled="isAnimating"
      >
      <span class="inline-flex items-center justify-center w-10 h-10 rounded-full bg-white/20 group-hover:bg-white/50  group-focus:ring-4 group-focus:ring-white group-focus:outline-none">
        <svg
            class="w-4 h-4 text-white dark:text-gray-800 rtl:rotate-180"
            aria-hidden="true"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 6 10"
        >
          <path
              stroke="white"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="m1 9 4-4-4-4"
          />
        </svg>
        <span class="sr-only">Next</span>
      </span>
      </button>
    </div>
    <div class="w-full py-2.5 flex flex-col md:flex-row px-4 md:px-0 justify-center items-center gap-2 md:gap-4 bg-[#0088CC] text-white font-medium text-center text-[12px] md:text-[18px]">
      <h3>La Unidad de Gestión Educativa Local de Yarowilca, pone a tu disposición  </h3>
      <a href="#tramites" class="hover:transform hover:scale-110 transition-transform duration-300 ease-in-out">Trámites y Servicios</a>
    </div>
  </div>
</template>

<style scoped>
.carousel-item {
  position: absolute;
  width: 100%;
  height: 100%;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.9s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-to,
.fade-leave-from {
  opacity: 1;
}
</style>