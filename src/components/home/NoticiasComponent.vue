<script setup>
import { Dot, MoveRight } from 'lucide-vue-next';
import { ref } from 'vue';
import noticesData from '@/assets/datahome/noticesdata.json';

const notices = ref(noticesData.notices);
</script>

<template>
<section class="container-general py-25">
    <div class="text-center">
      <h2 class="text-[20px] font-bold tracking-[16%] uppercase text-blue100">Comunicación y Noticias</h2>
      <p class="text-[32px] font-medium text-blue200">Mantente informado con nuestros comunicados y noticias.</p>
    </div>
    <div class="grid grid-cols-3 mt-16 gap-6">
        <div v-for="notice in notices" :key="notice.id" class="rounded-[10px] bg-blue-50 border grid grid-cols-1 gap-3 border-blue200/8 p-4">
            <div class="">
                <img :src="`/notices/${notice.image}`" class="rounded-[5px] w-full h-full object-cover" :alt="notice.title">
            </div>
            <div>
                <span class="flex gap-1 text-[14px] font-normal text-[#505050] mb-2">
                    <Dot class="w-5" />
                    {{ notice.date }}
                </span>
                <h3 class="text-[20px] font-semibold text-[#1F1F1F] line-clamp-3">{{ notice.title }}</h3>
                <a :href="notice.url" class="flex items-center gap-2.5 text-blue100 mt-4 hover:translate-x-2 transition-all duration-300 ease-in-out">Leer más <MoveRight /></a>
            </div>
        </div>
    </div>
</section>
</template>
<style scoped>
</style>