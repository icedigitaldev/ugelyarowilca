<script setup>
import { ref } from 'vue'
import servicios from '@/assets/datahome/servicesdata.json'

const serviciosData = ref(servicios.servicios)
</script>

<template>
  <section id="tramites" class="container-general py-10 md:py-16">
    <div class="text-center">
      <h2 class="title-section">Trámites digitales</h2>
      <p class="subtitle-section">Accede a tus trámites y servicios en línea</p>
    </div>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mt-8 md:mt-16">
      <!-- CARD -->
      <div v-for="(servicio, index) in serviciosData" :key="index">
        <a :href="servicio.link" target="_blank"
            class=" card-container border border-[#9AD6F3] shadow-card rounded-[10px] flex flex-col justify-center items-center gap-4 py-8 px-5 relative overflow-hidden">
          <div v-html="servicio.svgIcon"></div>
          <h3 class="text-[20px] font-medium text-black100 text-center mx-5 relative z-10">{{servicio.title}}</h3>
        </a>
      </div>

    </div>
  </section>
</template>

<style scoped>
.card-container {
  position: relative;
  transition: all 0.3s ease;
  background: white;
}

.card-container::before {
  content: '';
  position: absolute;
  bottom: 0;
  width: 0;
  height: 0;
  background: #E6F4FB; /* Color de fondo al hacer hover */
  transition: all 0.4s ease;
  z-index: 1;
}

.card-container:hover::before {
  width: 100%;
  height: 100%;
  border-radius: 10px;
}

.card-container > * {
  position: relative;
  z-index: 2;
}

/* Opcional: Efecto de escala en el contenido al hacer hover */
.card-container:hover {
  transform: translateY(-8px);
}
</style>