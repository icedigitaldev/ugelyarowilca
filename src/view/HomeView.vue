<script setup>
import PrincipalLayout from '../layout/PrincipalLayout.vue';
import HeroComponent from "@/components/home/HeroComponent.vue";
import ServiciosComponent from "@/components/home/ServiciosComponent.vue";
import MensajeDirector from "@/components/home/MensajeDirector.vue";
import PersonalComponente from '../components/home/PersonalComponente.vue';
import CallToActionComponent from '../components/home/CallToActionComponent.vue';
import NoticiasComponent from '../components/home/NoticiasComponent.vue';
import GalleryComponent from '../components/home/GalleryComponent.vue';
import EntidadesComponent from '@/components/home/EntidadesComponent.vue';
</script>
<template>
  <PrincipalLayout>
    <HeroComponent/>
    <ServiciosComponent/>
    <MensajeDirector/>
    <PersonalComponente/>
    <CallToActionComponent/>
    <NoticiasComponent/>
    <GalleryComponent/>
    <EntidadesComponent/>
  </PrincipalLayout>
</template>