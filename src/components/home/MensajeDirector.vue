<script setup>
import { ref } from 'vue'
import director from '@/assets/datahome/directordata.json'

const directorData = ref(director.director)
</script>

<template>
  <section class="bg-blue50 py-25 relative overflow-hidden">
    <!-- Fondo con patrón decorativo -->
    <img src="@/assets/img/bgdirector.svg" class="absolute opacity-10 z-0 w-full h-full object-cover pointer-events-none" />

    <div class="container-general relative px-[63px] flex flex-col lg:flex-row justify-between items-center gap-10 lg:gap-16">
      <!-- Columna de información -->
      <div class="max-w-[563px] z-10">
        <div class="mb-6 relative pl-4 border-l-4 border-blue200">
          <h2 class="font-semibold text-[32px] text-blue200 leading-tight">{{ directorData.name }}</h2>
          <p class="text-[18px] uppercase font-bold text-blue-900/70">{{ directorData.title }}</p>
        </div>

        <div class="bg-white/30 backdrop-blur-sm p-6 rounded-lg">
          <div v-for="(paragraph, index) in directorData.description" :key="index">
            <p class="text-[18px] font-normal mb-6 last:mb-0 text-blacktext leading-relaxed">{{ paragraph }}</p>
          </div>
        </div>
      </div>

      <!-- Columna de imagen -->
      <div class="relative rounded-[10px] z-10">
        <div class="shadow-lg rounded-[10px] overflow-hidden">
          <img
              :src="`/personal/${directorData.image}`"
              class="rounded-[10px] w-full object-cover"
              alt="Imagen de Director"
          />
          <div class="absolute bottom-0 rounded-b-[10px] w-full bg-blue200 py-2.5">
            <p class="font-semibold text-[14px] text-white text-center">{{ directorData.name }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.bg-blue50 {
  background-color: #f0f4ff;
}

.text-blue200 {
  color: #3b82f6;
}

.text-blacktext {
  color: #374151;
}

.bg-blue200 {
  background-color: #3b82f6;
}

@media (max-width: 1023px) {
  .container-general {
    padding-left: 1.5rem;
    padding-right: 1.5rem;
  }
}
</style>
