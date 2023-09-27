<template>
    <Layout>
      <Head title="Welcome" />
      <div class="cover-container">
        <div class="cover" :class="{'cover-animate': animate}">
          <h1>Willkommen,</h1>
          <p class="text-3xl">Schön, dass Sie hier sind!</p>
          <button @click="revealPortfolio" class="bg-indigo-400 px-4 py-2 rounded text-white mt-2">Let's go!</button>
        </div>
      </div>
    </Layout>
  </template>
  
  <script setup>
  import Layout from '@/Layouts/Layout.vue';
  import { Head } from '@inertiajs/vue3';
  import { ref } from 'vue';
  
  const animate = ref(false);
  
  const revealPortfolio = () => {
    animate.value = true;
    setTimeout(() => {
      window.location.href = '/portfolio';
    }, 2000); // The duration should match the CSS animation duration
  };
  </script>
  
  