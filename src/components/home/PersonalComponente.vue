<script setup>
import { ref } from 'vue'
import personal from '@/assets/datahome/personaldata.json'

const personalData = ref(personal.personal)
</script>
<template>
<section class="container-general py-25">
    <div class="text-center">
      <h2 class="text-[20px] font-bold tracking-[16%] uppercase text-blue100">Peronal administrativo</h2>
      <p class="text-[32px] font-medium text-blue200">Siempre listo para ayudarte con tus trámites y servicios.</p>
    </div>
    <div class="grid grid-cols-3 mt-16 gap-[25px]">
        <!-- Card -->
        <div v-for="(personal, index) in personalData" :key="index" class="grid grid-cols-1">
            <div class="h-full overflow-hidden rounded-t-[10px]">
                <img :src="`/personal/${personal.image}`" class=" object-cover h-full w-full rounded-t-[10px] hover:transform hover:scale-110 transition-transform duration-300 ease-in-out" alt="Imagen de Director" />
            </div>
            <div class="py-2.5 px-7 bg-blue50">
                <h3 class="text-[24px] font-bold text-blue200 text-center ">{{ personal.name }}</h3>
            </div>
            <div class="py-[14px] bg-blue200 flex justify-center items-center rounded-b-[10px]">
                <span class="text-white text-[15px] font-normal text-center"> {{ personal.title }} </span>
            </div>
        </div>
    </div>
</section>
</template>
<style scoped>
</style>