<script setup>
import { ref } from 'vue'
import director from '@/assets/datahome/directordata.json'

const directorData = ref(director.director)
</script>

<template>
  <section class="bg-blue50 py-25 relative overflow-hidden">
    <img src="@/assets/img/bgdirector.svg" class="absolute opacity-10 z-0 w-full h-full object-cover pointer-events-none" />
    <div class="container-general relative px-[63px] flex flex-row justify-between items-center">
      <div class="max-w-[563px] z-10">
        <div class="mb-6">
          <h2 class="font-semibold text-[32px] text-blue200">{{ directorData.name }}</h2>
          <p class="text-[18px] uppercase font-bold text-blue-900/70">{{ directorData.title }}</p>
        </div>
        <div v-for="(paragraph, index) in directorData.description" :key="index">
          <p class="text-[18px] font-normal mb-6 text-blacktext">{{ paragraph }}</p>
        </div>
      </div>
      <div class="relative rounded-[10px] z-10">
        <img :src="`/personal/${directorData.image}`" class="rounded-[10px]" alt="Imagen de Director" />
        <div class="absolute bottom-0 rounded-b-[10px] w-full bg-blue200 py-2.5">
          <p class="font-semibold text-[14px] text-white text-center">{{ directorData.name }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Puedes agregar estilos aquí si es necesario */
</style>
