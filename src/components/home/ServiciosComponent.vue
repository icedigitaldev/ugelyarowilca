<script setup>
import { ref } from 'vue';
import servicios from '@/assets/datahome/servicesdata.json';

const serviciosData = ref(servicios.servicios);
</script>

<template>
  <section id="tramites" class="bg-gray-50 py-14 px-4">
    <div class="max-w-6xl mx-auto">
      <div class="text-center mb-8">
        <h2 class="text-2xl md:text-3xl font-bold text-gray-800 mb-2">Trámites digitales</h2>
        <p class="text-base text-gray-600 max-w-xl mx-auto">Accede a tus trámites y servicios en línea de manera rápida y segura</p>
        <div class="h-1 w-16 bg-blue-400 mx-auto mt-3 rounded-full"></div>
      </div>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-5">
        <div v-for="(servicio, index) in serviciosData" :key="index" class="card-wrapper group">
          <a :href="servicio.link" target="_blank" class="card h-full flex flex-col items-center rounded-xl overflow-hidden bg-white">
            <div class="pt-6 pb-3">
              <div class="icon-wrapper bg-blue-50 p-4 rounded-full group-hover:bg-blue-100">
                <div class="w-10 h-10 flex items-center justify-center text-blue-600" v-html="servicio.svgIcon"></div>
              </div>
            </div>

            <div class="separator w-12 h-px bg-gray-100 group-hover:bg-blue-200"></div>

            <div class="p-4 w-full flex-1 flex flex-col justify-between">
              <h3 class="text-lg font-medium text-center text-gray-800 mb-3">
                {{ servicio.title }}
              </h3>

              <div class="flex justify-center">
                <span class="py-1 px-3 text-sm text-gray-500 group-hover:text-blue-600 flex items-center gap-1">
                  Acceder al trámite
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 transform group-hover:translate-x-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
                  </svg>
                </span>
              </div>
            </div>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.card-wrapper {
  perspective: 800px;
}

.card {
  box-shadow: 0 3px 10px -4px rgba(0,0,0,0.04);
  border: 1px solid rgba(229, 231, 235, 0.8);
  transition: all 0.25s ease;
  min-height: 200px;
}

.card-wrapper:hover .card {
  box-shadow: 0 12px 20px -8px rgba(0,0,0,0.06);
  transform: translateY(-5px);
  border-color: rgba(191, 219, 254, 0.7);
}

.icon-wrapper, .separator {
  transition: all 0.25s ease;
}

.card-wrapper:hover .separator {
  width: 50%;
}
</style>
