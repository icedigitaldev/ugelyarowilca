<script setup>
import { ref, computed } from 'vue'
import entidades from '@/assets/datahome/entidadesdata.json'

const entidadesData = ref(entidades.entidades)
// Duplicamos para lograr el efecto infinito
const duplicatedEntidades = computed(() => [...entidadesData.value, ...entidadesData.value])

const sliderWrapperRef = ref(null)
const sliderRef = ref(null)
const isDragging = ref(false)
let startX = 0
let scrollLeft = 0

function onDragStart(e) {
  isDragging.value = true
  startX = e.pageX || e.touches?.[0].pageX
  scrollLeft = sliderWrapperRef.value.scrollLeft
}

function onDragging(e) {
  if (!isDragging.value) return
  e.preventDefault()
  const x = e.pageX || e.touches?.[0].pageX
  const walk = x - startX
  sliderWrapperRef.value.scrollLeft = scrollLeft - walk
}

function onDragEnd() {
  isDragging.value = false
}
</script>

<template>
  <section class=" container-general py-25">

    <div
      class="slider-wrapper relative"
      ref="sliderWrapperRef"
      @mousedown="onDragStart"
      @touchstart="onDragStart"
      @mousemove="onDragging"
      @touchmove="onDragging"
      @mouseup="onDragEnd"
      @mouseleave="onDragEnd"
      @touchend="onDragEnd"
    >

    <div
          class="pointer-events-none absolute top-0 left-0 h-full w-[6rem] md:w-[14rem] z-[999]"
          style="background: linear-gradient(to right, white, transparent);"
        ></div>
        <div
          class="pointer-events-none absolute top-0 right-0 h-full w-[6rem] md:w-[14rem] z-[999]"
          style="background: linear-gradient(to left, white, transparent);"
        ></div>

      <div class="slider flex items-center" ref="sliderRef" :class="{ paused: isDragging }">
        <div
          v-for="(item, index) in duplicatedEntidades"
          :key="index"
          class="slide-item"
        >
          <a :href="item.url" target="_blank" class="w-40" rel="noopener noreferrer">
            <img :src="`/entidades/${item.logo}`" class="w-full h-full" alt="" />
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.slider-wrapper {
  position: relative;
  width: 100%;
  overflow: hidden;
}

/* Eliminamos el degradado en los costados. 
   Si deseas ocultarlos en lugar de borrarlos, 
   puedes comentar o remover los pseudo-elementos. */
/* .slider-wrapper::before,
.slider-wrapper::after {
  content: "";
  position: absolute;
  top: 0;
  width: 100px;
  height: 100%;
  z-index: 2;
  pointer-events: none;
}

.slider-wrapper::before {
  left: 0;
  background: linear-gradient(to right, white 0%, transparent 100%);
}

.slider-wrapper::after {
  right: 0;
  background: linear-gradient(to left, white 0%, transparent 100%);
} */

.slider {
  display: inline-flex;
  /* Hacemos la animación más lenta: 40s */
  animation: scroll-left 40s linear infinite;
}

.slider:hover,
.slider.paused {
  animation-play-state: paused;
}

/* Aumentamos la separación entre entidades (margin-right) */
.slide-item {
  min-width: 200px;
  margin-right: 60px;
  filter: grayscale(100%);
  transition: filter 0.3s;
}

.slide-item:hover {
  filter: grayscale(0%);
}

.slide-item img {
  display: block;
  width: 100%;
  height: auto;
}

@keyframes scroll-left {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-50%);
  }
}
</style>
