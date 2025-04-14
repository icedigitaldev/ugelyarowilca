<template>
    <div class="w-full p-4 relative">
      <!-- Contenedor principal con perspectiva 3D -->
      <div class="relative w-full h-[20rem] overflow-hidden" style="perspective: 1400px;">
        
        <!-- Nieblas blancas en los costados -->
        <div
          class="pointer-events-none absolute top-0 left-0 h-full w-[6rem] md:w-[14rem] z-[999]"
          style="background: linear-gradient(to right, white, transparent);"
        ></div>
        <div
          class="pointer-events-none absolute top-0 right-0 h-full w-[6rem] md:w-[14rem] z-[999]"
          style="background: linear-gradient(to left, white, transparent);"
        ></div>
  
        <!-- Tarjetas -->
        <div
          v-for="(card, index) in cards"
          :key="index"
          class="absolute top-1/2 left-1/2 transform-gpu"
          :style="getCardStyle(index)"
          @click.stop="offsetFor(index) === 0 ? openModal(index) : null"
        >
          <div
            class="relative w-40 h-30 md:w-96  md:h-80 rounded-lg overflow-hidden shadow-lg pointer-events-auto"
            :style="{
              backgroundImage: 'url(' + card.image + ')',
              backgroundSize: 'cover',
              backgroundPosition: 'center'
            }"
          >
            <transition name="fadeOverlay">
              <!-- Oscurecemos las tarjetas que no están al frente SIN transparencia -->
              <div
                v-if="offsetFor(index) !== 0"
                class="absolute inset-0 bg-black/60 pointer-events-none"
              ></div>
            </transition>
          </div>
        </div>
  
        <!-- Botón anterior -->
        <button
          class="absolute top-1/2 left-4 transform -translate-y-1/2 bg-gray-800/50 hover:bg-gray-800 transition-colors duration-300 ease-in-out cursor-pointer text-white px-3 py-1 rounded-full z-[1000]"
          @click="prevSlide"
        >
          <ChevronLeft />
        </button>
  
        <!-- Botón siguiente -->
        <button
          class="absolute top-1/2 right-4 transform -translate-y-1/2 bg-gray-800/50 hover:bg-gray-800 transition-colors duration-300 ease-in-out cursor-pointer text-white px-3 py-1 rounded-full z-[1000]"
          @click="nextSlide"
        >
          <ChevronRight />
        </button>
      </div>
  
      <!-- Modal con transición de opacidad -->
      <transition name="fadeModal">
        <div
          v-if="showModal"
          class="fixed inset-0 flex items-center justify-center bg-black/60 z-50"
          @click.self="closeModal"
        >
          <div class="relative max-w-3xl max-h-[80vh] w-auto h-auto flex items-center justify-center">
            <!-- Botón cerrar -->
            <button
              class="absolute bg-gray-800/50 hover:bg-gray-800 transition-colors duration-300 ease-in-out cursor-pointer p-2 rounded-full top-2 right-2 text-white text-2xl font-bold z-10"
              @click="closeModal"
            >
              <CircleX />
            </button>
            <!-- Botón anterior (modal) -->
            <button
              class="absolute -left-6 text-white text-xl font-bold z-10 bg-gray-800/50 hover:bg-gray-800 transition-colors duration-300 ease-in-out cursor-pointer p-2 rounded-full"
              @click.stop="modalPrev"
            >
              <ChevronLeft />
            </button>
            <!-- Imagen en modal -->
            <img
              :src="cards[selectedIndex].image"
              alt="Selected Image"
              class="max-w-full max-h-[90vh] object-contain rounded-xl"
            />
            <!-- Botón siguiente (modal) -->
            <button
              class="absolute -right-6 text-white text-xl font-bold z-10 bg-gray-800/50 hover:bg-gray-800 transition-colors duration-300 ease-in-out cursor-pointer p-2 rounded-full"
              @click.stop="modalNext"
            >
              <ChevronRight />
            </button>
          </div>
        </div>
      </transition>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted, onUnmounted } from 'vue'
  import { ChevronRight, ChevronLeft, CircleX } from "lucide-vue-next"
  
  function useScreenWidth() {
  const screenWidth = ref(window.innerWidth);

  const updateScreenWidth = () => {
    screenWidth.value = window.innerWidth;
  };

  onMounted(() => {
    window.addEventListener('resize', updateScreenWidth);
  });

  onUnmounted(() => {
    window.removeEventListener('resize', updateScreenWidth);
  });

  return screenWidth;
}
const screenWidth = useScreenWidth();

  const cards = ref([
    { image: "/notices/notice1.jpg" },
    { image: "/notices/notice2.jpg" },
    { image: "/notices/notice3.jpg" },
    { image: "/notices/notice4.jpg" },
    { image: "/notices/notice5.jpg" },
    { image: "/notices/notice6.jpg" },
    { image: "/notices/notice7.jpg" },
    { image: "/notices/notice8.jpg" },
    { image: "/notices/notice9.jpg" },
    { image: "/notices/notice10.jpg" },
    { image: "/notices/notice11.jpg" },
  ])
  
  const currentIndex = ref(0)
  const showModal = ref(false)
  const selectedIndex = ref(0)

  function offsetFor(index) {
    const total = cards.value.length
    let offset = index - currentIndex.value
    if (offset > total / 2) {
      offset -= total
    } else if (offset < -total / 2) {
      offset += total
    }
    return offset
  }
  
  /**
   * Genera los estilos dinámicos (transform, zIndex, opacidad, etc.)
   * para lograr un efecto 3D y fade suave.
   */
  function getCardStyle(index) {
    const offset = offsetFor(index)
  
    // Ajusta aquí el rango máximo de visibilidad y la suavidad del fade
    const maxOffset = 3
    const fade = 1 - (Math.abs(offset) / maxOffset)
    // Si fade queda por debajo de 0, forzamos 0
    const opacity = fade < 0 ? 0 : fade
  
    // Ajusta traslación y rotación para un efecto 3D suave
    const angle = offset * 15            // rotación en Y
    const translateX = offset * 230      // desplazamiento horizontal
    const translateZ = -Math.abs(offset) * 80
    let scale;
    if(screenWidth.value < 768){
        scale = 1.5 - Math.min(Math.abs(offset) * 0.06, 0.25)
    }else{
        scale = 1 - Math.min(Math.abs(offset) * 0.06, 0.25)
    }
    const zIndex = 100 - Math.abs(offset)
  
    return {
      transform: `
        translate(-50%, -50%)
        translateX(${translateX}px)
        rotateY(${angle}deg)
        translateZ(${translateZ}px)
        scale(${scale})
      `,
      zIndex,
      opacity,
      transition: 'transform 0.8s ease-in-out, opacity 0.8s ease-in-out',
      pointerEvents: offset === 0 ? 'auto' : 'none'
    }
  }
  
  function nextSlide() {
    currentIndex.value = (currentIndex.value + 1) % cards.value.length
  }
  
  function prevSlide() {
    currentIndex.value = (currentIndex.value - 1 + cards.value.length) % cards.value.length
  }
  
  function openModal(index) {
    selectedIndex.value = index
    showModal.value = true
  }
  
  function closeModal() {
    showModal.value = false
  }
  
  function modalNext() {
    selectedIndex.value = (selectedIndex.value + 1) % cards.value.length
  }
  
  function modalPrev() {
    selectedIndex.value = (selectedIndex.value - 1 + cards.value.length) % cards.value.length
  }
  </script>
  
  <style scoped>
  .transform-gpu {
    transform-style: preserve-3d;
  }
  
  /* Transición para el overlay de las tarjetas */
  .fadeOverlay-enter-active,
  .fadeOverlay-leave-active {
    transition: opacity 0.5s ease;
  }
  .fadeOverlay-enter-from,
  .fadeOverlay-leave-to {
    opacity: 0;
  }
  .fadeOverlay-enter-to,
  .fadeOverlay-leave-from {
    opacity: 1;
  }
  
  /* Transición de opacidad para mostrar/ocultar el modal */
  .fadeModal-enter-active,
  .fadeModal-leave-active {
    transition: opacity 0.5s ease;
  }
  .fadeModal-enter-from,
  .fadeModal-leave-to {
    opacity: 0;
  }
  .fadeModal-enter-to,
  .fadeModal-leave-from {
    opacity: 1;
  }
  </style>
  