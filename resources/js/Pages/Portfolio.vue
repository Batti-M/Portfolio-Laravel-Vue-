<template>
   <Layout>

      <Head title="Home" />
      <Header />
      <Projekt :imageSrc="'path_to_your_image.jpg'" :description="'This is an image description'" />
      <UeberMich />
   </Layout>
</template>

<script setup>
import Layout from '@/Layouts/Layout.vue';
import Header from './Header.vue';
import { Head } from '@inertiajs/vue3';
import UeberMich from './UeberMich.vue';
import Projekt from '../Components/Projekt.vue';
</script>

<style lang="scss" scoped>

</style>