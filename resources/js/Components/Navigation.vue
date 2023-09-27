<script setup>
import { ref } from 'vue';
import { Link } from '@inertiajs/vue3';

const showingNavigationDropdown = ref(false);
</script>

<template>
    <nav class="hidden sm:block space-x-8 flex justify-end">

        <div class="hidden sm:block space-x-8 flex justify-end">
            
            <Link href="#" class="text-gray-200 text-xl font-bold  p-2 "> Home </Link>
            <Link href="#" class="text-gray-200 text-xl font-bold  p-2 "> Projekte </Link>
            <Link href="#" class="text-gray-200 text-xl font-bold  p-2 "> Über mich </Link>

        </div>
        
    </nav>
</template>