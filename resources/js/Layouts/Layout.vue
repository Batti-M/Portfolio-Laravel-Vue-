<script setup>

import Navigation from '@/Components/Navigation.vue';


</script>

<template>
   
        <div class="min-h-screen bg-gradient-to-b from-indigo-300">
            <!-- Page Navigation -->
            
            <!-- Page Content -->
            <main class="h-auto bg-gradient-to-b from-indigo-300 grid justify-items-center content-center border">
                <slot />
            </main>
        </div>
    
</template>
