<script setup>
import {ChevronDown, ChevronRight} from 'lucide-vue-next'
</script>

<template>
  <header class="py-2.5 bg-white shadow-header fixed top-0 w-full z-1000 ">
    <div class="container-general flex flex-row justify-between">
      <div class="w-[130px] h-[56px]">
        <img src="@/assets/img/logo.png" alt="logo">
      </div>
      <nav class="flex flex-row items-center text-[14px] font-medium">
        <a href="/" class="   link-nav">Inicio</a>
        <div class="dropdown h-full">
          <div tabindex="0" role="button" class="flex link-nav h-full items-center gap-2.5 cursor-pointer uppercase ">
            Ugel
            <ChevronDown class="w-4"/>
          </div>
          <ul tabindex="0" class="dropdown-content menu bg-base-100 rounded-box z-1 w-52 p-2 shadow-sm">
            <li><a>Bienvenida</a></li>
            <li><a>Misión</a></li>
            <li><a>Juridicción</a></li>
            <li><a>Reglamento interno de trabajo</a></li>
            <li><a>RUC UGEL Yarowilca</a></li>
            <li><a>Convocatorias</a></li>
          </ul>
        </div>
        <div class="dropdown h-full">
          <div tabindex="0" role="button" class="flex link-nav h-full items-center gap-2.5 cursor-pointer uppercase ">
            Dirección
            <ChevronDown class="w-4"/>
          </div>
          <ul tabindex="0" class="dropdown-content menu bg-base-100 rounded-box z-1 w-52 p-2 shadow-sm">
            <li><a>Oficina de dirección</a></li>
            <li><a>Organigrama</a></li>
            <li><a>Funciones</a></li>
          </ul>
        </div>
        <div class="dropdown h-full">
          <div tabindex="0" role="button" class="flex link-nav h-full items-center gap-2.5 cursor-pointer uppercase ">
            Áreas
            <ChevronDown class="w-4"/>
          </div>
          <ul tabindex="0" class="dropdown-content menu bg-base-100 rounded-box z-1 w-52 p-2 shadow-sm">
            <li><a>Gestión Administrativa</a></li>
            <li><a>Gestión Institucional</a></li>
            <li><a>Gestión Pedagógica</a></li>
          </ul>
        </div>
        <div class="dropdown h-full">
          <div tabindex="0" role="button" class="flex link-nav h-full items-center gap-2.5 cursor-pointer uppercase ">
            documentos de gestión
            <ChevronDown class="w-4"/>
          </div>
          <ul tabindex="0" class="dropdown-content menu bg-base-100 rounded-box z-1 w-52 p-2 shadow-sm">
            <li><a>ROF</a></li>
            <li><a>MOF</a></li>
            <li><a>TUPA</a></li>
            <li><a>Planes 2025</a></li>
            <li><a>Resoluciones</a></li>
          </ul>
        </div>
        <div class="dropdown h-full">
          <div tabindex="0" role="button" class="flex link-nav h-full items-center gap-2.5 cursor-pointer uppercase ">
            servicios
            <ChevronDown class="w-4"/>
          </div>
          <ul tabindex="0" class="dropdown-content menu bg-base-100 rounded-box z-1 w-52 p-2 shadow-sm">
            <li><a>Dirección Institucional</a></li>
            <li><a>Mesa de Partes</a></li>
            <li><a>Boletas UGEL</a></li>
            <li><a>Transparencia</a></li>
            <li><a>Libro de reclamaciones</a></li>
          </ul>
        </div>
        <a href="https://www.transparencia.gob.pe/enlaces/pte_transparencia_enlaces.aspx?id_entidad=18837" target="_blank" class="ml-5 rounded-[10px] ">
          <img src="@/assets/img/logotransparencia.svg" class="w-[98px]" alt="Descripción de la imagen">
        </a>
      </nav>
    </div>
  </header>
</template>

<style scoped>
</style>
