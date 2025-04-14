<script setup>
import { ref } from 'vue'
import personal from '@/assets/datahome/personaldata.json'

const personalData = ref(personal.personal)
</script>

<template>
  <section class="container-general py-25">
    <div class="text-center mb-8">
      <h2 class="text-2xl md:text-3xl font-bold text-gray-800 mb-2">Personal administrativo</h2>
      <p class="text-base text-gray-600 max-w-xl mx-auto">Siempre listo para ayudarte con tus trámites y servicios.</p>
      <div class="h-1 w-16 bg-blue-400 mx-auto mt-3 rounded-full"></div>
    </div>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 mt-16 gap-[25px]">
      <!-- Card -->
      <div
          v-for="(personal, index) in personalData"
          :key="index"
          class="grid grid-cols-1 group rounded-[10px] shadow-lg hover:shadow-xl transition-all duration-300"
      >
        <div class="h-72 overflow-hidden rounded-t-[10px] relative">
          <img
              :src="`/personal/${personal.image}`"
              class="object-cover h-full w-full rounded-t-[10px] transition-transform duration-500 group-hover:scale-110"
              :alt="`Imagen de ${personal.name}`"
          />
          <div class="absolute inset-0 bg-blue200/20 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
        </div>
        <div class="py-2.5 px-7 bg-blue50 border-l-4 border-blue100">
          <h3 class="text-[24px] font-bold text-blue200 text-center">{{ personal.name }}</h3>
        </div>
        <div class="py-[14px] bg-blue200 flex justify-center items-center rounded-b-[10px] group-hover:bg-blue100 transition-colors duration-300">
          <span class="text-white text-[15px] font-normal text-center">{{ personal.title }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.container-general {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}
</style>
