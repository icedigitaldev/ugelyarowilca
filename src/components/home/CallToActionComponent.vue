<script setup>
import { ref } from 'vue'
import callactionData from '@/assets/datahome/callactiondata.json'

const statsData = ref(callactionData.stats)
</script>
<template>
<section class="">
    <div class="calltoaction relative h-110 flex justify-center items-center">
        <div class="bg-blue100/70 absolute w-full h-full z-0"></div>
        <div class="max-w-[832.37px] flex flex-col items-center gap-8 z-10">
            <div>
                <svg xmlns="http://www.w3.org/2000/svg" width="76" height="76" viewBox="0 0 76 76" fill="none">
                    <path d="M24.2891 53.5363C23.0162 52.2634 23.6797 52.6223 20.6094 51.8005C19.2164 51.427 17.9917 50.7092 16.8843 49.8493L10.2383 66.1442C9.59526 67.7219 10.7964 69.4358 12.4986 69.3713L20.2168 69.0769L25.5254 74.6843C26.6973 75.9206 28.754 75.5354 29.397 73.9577L37.0215 55.2634C35.4336 56.1482 33.6714 56.6667 31.8492 56.6667C28.9927 56.6667 26.3091 55.5549 24.2891 53.5363ZM66.1368 66.1442L59.4908 49.8493C58.3833 50.7107 57.1587 51.427 55.7657 51.8005C52.6792 52.6267 53.356 52.2663 52.086 53.5363C50.066 55.5549 47.3809 56.6667 44.5245 56.6667C42.7022 56.6667 40.94 56.1467 39.3521 55.2634L46.9766 73.9577C47.6197 75.5354 49.6778 75.9206 50.8482 74.6843L56.1582 69.0769L63.8765 69.3713C65.5787 69.4358 66.7798 67.7204 66.1368 66.1442ZM48.5879 50.2214C50.8262 47.9436 51.0826 48.1398 54.2701 47.2712C56.3047 46.716 57.8956 45.0974 58.4405 43.0261C59.5362 38.8659 59.252 39.3684 62.2417 36.3244C63.7315 34.8083 64.313 32.5979 63.7681 30.5266C62.6739 26.3693 62.6724 26.9494 63.7681 22.7878C64.313 20.7165 63.7315 18.5061 62.2417 16.99C59.252 13.946 59.5362 14.447 58.4405 10.2883C57.8956 8.217 56.3047 6.59835 54.2701 6.04317C50.1861 4.92843 50.6783 5.21993 47.6856 2.17452C46.1958 0.658408 44.0235 0.065146 41.9888 0.620322C37.9063 1.7336 38.4761 1.73507 34.3863 0.620322C32.3516 0.065146 30.1792 0.656943 28.6895 2.17452C25.6998 5.21847 26.1919 4.92843 22.1065 6.04317C20.0718 6.59835 18.481 8.217 17.9361 10.2883C16.8418 14.447 17.1246 13.946 14.1348 16.99C12.6451 18.5061 12.0621 20.7165 12.6084 22.7878C13.7027 26.9421 13.7041 26.362 12.6084 30.5251C12.0635 32.5964 12.6451 34.8068 14.1348 36.3244C17.1246 39.3684 16.8404 38.8659 17.9361 43.0261C18.481 45.0974 20.0718 46.716 22.1065 47.2712C25.3848 48.1647 25.6294 48.0241 27.7872 50.2214C29.7251 52.1945 32.7442 52.5476 35.0733 51.0739C36.0047 50.4827 37.0851 50.1687 38.1883 50.1687C39.2915 50.1687 40.3719 50.4827 41.3033 51.0739C43.6309 52.5476 46.6499 52.1945 48.5879 50.2214ZM24.3682 26.1921C24.3682 18.424 30.5557 12.1267 38.1875 12.1267C45.8194 12.1267 52.0069 18.424 52.0069 26.1921C52.0069 33.9602 45.8194 40.2575 38.1875 40.2575C30.5557 40.2575 24.3682 33.9602 24.3682 26.1921Z" fill="white"/>
                </svg>
            </div>
            <h2 class="text-[32px] font-semibold text-white uppercase">
                UGEL YAROWILCA
            </h2>
            <p class="text-white font-medium text-[22px] text-center">
                Nos encargamos de garantizar la calidad educativa, brindando apoyo y gestionando los recursos necesarios para el bienestar de todas nuestras escuelas públicas. ¡Juntos, hacemos un futuro mejor!
            </p>
        </div>
    </div>
    <div class="py-7 grid grid-cols-4 bg-gray50">
       <div v-for="(stat, index) in statsData" :key="index" class="container-general">
        <div class="flex flex-col items-center gap-[25px]">
            <img :src="stat.image" class="w-15" :alt="stat.label"/>
            <div class="flex flex-col items-center gap-2.5">
                <h3 class="text-black100 font-semibold text-[25px]">{{ stat.count }}</h3>
                <p class="text-gray100 font-medium text-[18px] uppercase">{{ stat.label }}</p>
            </div>
        </div>
       </div>
    </div>
</section>
</template>
<style scoped>
.calltoaction{
    background: url(@/assets/img/callaction.png);
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    background-attachment: fixed;
}
</style>