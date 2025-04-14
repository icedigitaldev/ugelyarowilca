<script setup>
import { ref } from 'vue';
import { ChevronRight, Clock, Mail, Phone, MapPin } from "lucide-vue-next";

const currentYear = ref(new Date().getFullYear());
</script>

<template>
<footer class="bg-blue200 relative">
    <div class="container-general relative py-12">
        <div class="w-full h-2 bg-blue100 absolute top-0"></div>
        <div class="grid grid-cols-12 px-4">
            <div class="col-span-3 flex flex-col gap-4">
                <img src="@/assets/img/logofooter.png" alt="logo" class="w-52">
                <div class="">
                    <h3 class="text-white font-semibold text-[24px]">Horarios de atención</h3>
                    <div class="flex flex-col gap-3 mt-3">
                        <span class="flex items-center gap-1 text-white text-[16px]"><ChevronRight class="text-yellow-300 w-4" />Lunes a Jueves:</span>
                        <ul class="ml-12">
                            <li class="text-white text-[14px] flex items-center gap-1"><Clock class="text-yellow-300 w-4" />8:00 AM - 1:00 PM</li>
                            <li class="text-white text-[14px] flex items-center gap-1"><Clock class="text-yellow-300 w-4" />2:30 PM - 5:30 PM</li>
                        </ul>
                    </div>
                    <div class="flex flex-col gap-3 mt-3">
                        <span class="flex items-center gap-1 text-white text-[16px]"><ChevronRight class="text-yellow-300 w-4" />Viernes:</span>
                        <ul class="ml-12">
                            <li class="text-white text-[14px] flex items-center gap-1"><Clock class="text-yellow-300 w-4" />8:00 AM - 1:00 PM</li>
                            <li class="text-white text-[14px] flex items-center gap-1"><Clock class="text-yellow-300 w-4" />1:45 PM - 4:45 PM</li>
                        </ul>
                    </div>
                </div>
            </div>
            <div class="col-span-3">
                <h3 class="text-white font-semibold text-[24px]">Oficinas y Áreas</h3>
                <ul class="mt-5 flex flex-col gap-4 text-[14px]">
                    <li class="text-white"><a href="" class="flex items-center gap-1"><ChevronRight class="text-yellow-300 w-4" />Dirección</a></li>
                    <li class="text-white"><a href="" class="flex items-center gap-1"><ChevronRight class="text-yellow-300 w-4" />Gestión Administrativa</a></li>
                    <li class="text-white"><a href="" class="flex items-center gap-1"><ChevronRight class="text-yellow-300 w-4" />Gestión Institucional</a></li>
                    <li class="text-white"><a href="" class="flex items-center gap-1"><ChevronRight class="text-yellow-300 w-4" />Gestión Pedagógica</a></li>
                </ul>
            </div>
            <div class="col-span-3">
                <h3 class="text-white font-semibold text-[24px]">Servicios</h3>
                <ul class="mt-5 flex flex-col gap-4 text-[14px]">
                    <li class="text-white"><a href="" class="flex items-center gap-1"><ChevronRight class="text-yellow-300 w-4" />Directorio Institucional</a></li>
                    <li class="text-white"><a href="" class="flex items-center gap-1"><ChevronRight class="text-yellow-300 w-4" />Mi boleta</a></li>
                    <li class="text-white"><a href="" class="flex items-center gap-1"><ChevronRight class="text-yellow-300 w-4" />Mesa de Parte Virtual</a></li>
                    <li class="text-white"><a href="" class="flex items-center gap-1"><ChevronRight class="text-yellow-300 w-4" />FUT UGEL Yarowilca</a></li>
                    <li class="text-white"><a href="" class="flex items-center gap-1"><ChevronRight class="text-yellow-300 w-4" />Libro de reclamaciones</a></li>
                </ul>
            </div>
            <div class="col-span-3">
                <h3 class="text-white font-semibold text-[24px]">Contáctenos</h3>
                <ul class="mt-5 flex flex-col gap-4 text-[14px]">
                    <li class="text-white"><a href="" class="flex items-center gap-1"><MapPin class="text-yellow-300 w-4" />Jr. Huánuco N° 223 - Chavinillo</a></li>
                    <li class="text-white"><a href="" class="flex items-center gap-1"><Phone class="text-yellow-300 w-4" />940 513 442</a></li>
                    <li class="text-white"><a href="" class="flex items-center gap-1"><Mail class="text-yellow-300 w-4" />informatica@ugelyarowilca.edu.pe</a></li>
                </ul>
                <div class="flex items-center gap-2.5 mt-4">
                    <a href="https://www.facebook.com/UgelYarowilca310c" class="rounded-full w-fit h-fit group bg-white/15 hover:bg-white transition-colors duration-300 ease-in-out p-3"><svg class="h-fit text-white group-hover:text-blue200  w-6" xmlns="http://www.w3.org/2000/svg" width="128" height="128" viewBox="0 0 24 24"><path fill="currentColor" d="M9.198 21.5h4v-8.01h3.604l.396-3.98h-4V7.5a1 1 0 0 1 1-1h3v-4h-3a5 5 0 0 0-5 5v2.01h-2l-.396 3.98h2.396z"/></svg></a>
                    <a href="https://api.whatsapp.com/send?phone=51940513442&text=Hola%20con%20%C3%81rea%20de%20Inform%C3%A1tica%20de%20la%20Ugel%20Yarowilca...%3F" class="rounded-full w-fit h-fit group bg-white/15 hover:bg-white transition-colors duration-300 ease-in-out p-3"><svg class="h-fit text-white group-hover:text-blue200  w-6" xmlns="http://www.w3.org/2000/svg" width="128" height="128" viewBox="0 0 24 24"><path fill="currentColor" d="M12.04 2c-5.46 0-9.91 4.45-9.91 9.91c0 1.75.46 3.45 1.32 4.95L2.05 22l5.25-1.38c1.45.79 3.08 1.21 4.74 1.21c5.46 0 9.91-4.45 9.91-9.91c0-2.65-1.03-5.14-2.9-7.01A9.82 9.82 0 0 0 12.04 2m.01 1.67c2.2 0 4.26.86 5.82 2.42a8.23 8.23 0 0 1 2.41 5.83c0 4.54-3.7 8.23-8.24 8.23c-1.48 0-2.93-.39-4.19-1.15l-.3-.17l-3.12.82l.83-3.04l-.2-.32a8.2 8.2 0 0 1-1.26-4.38c.01-4.54 3.7-8.24 8.25-8.24M8.53 7.33c-.16 0-.43.06-.66.31c-.22.25-.87.86-.87 2.07c0 1.22.89 2.39 1 2.56c.14.17 1.76 2.67 4.25 3.73c.59.27 1.05.42 1.41.53c.59.19 1.13.16 1.56.1c.48-.07 1.46-.6 1.67-1.18s.21-1.07.15-1.18c-.07-.1-.23-.16-.48-.27c-.25-.14-1.47-.74-1.69-.82c-.23-.08-.37-.12-.56.12c-.16.25-.64.81-.78.97c-.15.17-.29.19-.53.07c-.26-.13-1.06-.39-2-1.23c-.74-.66-1.23-1.47-1.38-1.72c-.12-.24-.01-.39.11-.5c.11-.11.27-.29.37-.44c.13-.14.17-.25.25-.41c.08-.17.04-.31-.02-.43c-.06-.11-.56-1.35-.77-1.84c-.2-.48-.4-.42-.56-.43c-.14 0-.3-.01-.47-.01"/></svg></a>
                    <a href="https://www.youtube.com/@ugelyarowilca" class="rounded-full w-fit h-fit group bg-white/15 hover:bg-white transition-colors duration-300 ease-in-out p-3"><svg class="h-fit text-white group-hover:text-blue200  w-6" xmlns="http://www.w3.org/2000/svg" width="128" height="128" viewBox="0 0 24 24"><path fill="currentColor" d="m10 15l5.19-3L10 9zm11.56-7.83c.13.47.22 1.1.28 1.9c.07.8.1 1.49.1 2.09L22 12c0 2.19-.16 3.8-.44 4.83c-.25.9-.83 1.48-1.73 1.73c-.47.13-1.33.22-2.65.28c-1.3.07-2.49.1-3.59.1L12 19c-4.19 0-6.8-.16-7.83-.44c-.9-.25-1.48-.83-1.73-1.73c-.13-.47-.22-1.1-.28-1.9c-.07-.8-.1-1.49-.1-2.09L2 12c0-2.19.16-3.8.44-4.83c.25-.9.83-1.48 1.73-1.73c.47-.13 1.33-.22 2.65-.28c1.3-.07 2.49-.1 3.59-.1L12 5c4.19 0 6.8.16 7.83.44c.9.25 1.48.83 1.73 1.73"/></svg></a>
                    <a href="https://www.instagram.com/ugelyarowilca/" class="rounded-full w-fit h-fit group bg-white/15 hover:bg-white transition-colors duration-300 ease-in-out p-3"><svg class="h-fit text-white group-hover:text-blue200  w-6" xmlns="http://www.w3.org/2000/svg" width="128" height="128" viewBox="0 0 24 24"><path fill="currentColor" d="M7.8 2h8.4C19.4 2 22 4.6 22 7.8v8.4a5.8 5.8 0 0 1-5.8 5.8H7.8C4.6 22 2 19.4 2 16.2V7.8A5.8 5.8 0 0 1 7.8 2m-.2 2A3.6 3.6 0 0 0 4 7.6v8.8C4 18.39 5.61 20 7.6 20h8.8a3.6 3.6 0 0 0 3.6-3.6V7.6C20 5.61 18.39 4 16.4 4zm9.65 1.5a1.25 1.25 0 0 1 1.25 1.25A1.25 1.25 0 0 1 17.25 8A1.25 1.25 0 0 1 16 6.75a1.25 1.25 0 0 1 1.25-1.25M12 7a5 5 0 0 1 5 5a5 5 0 0 1-5 5a5 5 0 0 1-5-5a5 5 0 0 1 5-5m0 2a3 3 0 0 0-3 3a3 3 0 0 0 3 3a3 3 0 0 0 3-3a3 3 0 0 0-3-3"/></svg></a>
                    <a href="https://www.tiktok.com/@ugelyarowilca310" class="rounded-full w-fit h-fit group bg-white/15 hover:bg-white transition-colors duration-300 ease-in-out p-3"><svg class="h-fit text-white group-hover:text-blue200  w-6" xmlns="http://www.w3.org/2000/svg" width="128" height="128" viewBox="0 0 24 24"><path fill="currentColor" d="M12.438 2.017C13.53 2 14.613 2.008 15.696 2c.067 1.275.525 2.575 1.459 3.475c.933.925 2.25 1.35 3.533 1.492v3.358c-1.2-.042-2.408-.292-3.5-.808c-.475-.217-.917-.492-1.35-.775c-.008 2.433.008 4.866-.017 7.291a6.36 6.36 0 0 1-1.125 3.283c-1.091 1.6-2.983 2.642-4.924 2.675c-1.192.067-2.384-.258-3.4-.858c-1.684-.992-2.867-2.808-3.042-4.758a16 16 0 0 1-.008-1.242c.15-1.583.933-3.1 2.15-4.133c1.383-1.2 3.316-1.775 5.125-1.433c.016 1.233-.034 2.466-.034 3.7c-.825-.267-1.791-.192-2.516.308a2.9 2.9 0 0 0-1.134 1.458c-.175.425-.125.892-.116 1.342c.2 1.366 1.516 2.516 2.916 2.392c.934-.009 1.825-.55 2.309-1.342c.158-.275.333-.559.341-.884c.084-1.491.05-2.975.059-4.466c.008-3.358-.009-6.708.016-10.058"/></svg></a>
                </div>
            </div>
        </div>
    </div>
    <div class="container-general py-5 flex justify-center text-white text-[12px] border-t-2 border-gray-100/20">
        <p>&copy; {{ currentYear }} UGEL Yarowilca </p>
    </div>
</footer>
</template>
<style scoped>
</style>