<template>
    <div class="flex m-4 p-4">
        <header v-for="char in projectHeader" :key="char" class="text-6xl shadow-sm  flex p-4" @mouseover="startAnimation"
            @animationend="endAnimation">
            {{ char }}
        </header>
    </div>

    <div class="grid lg:grid-cols-3 w-3/4 gap-7 mt-auto">
        <div class="hover-image border m-2 p-2 shadow-xl flex flex-col justify-around rounded-xl bg-gradient-to-b from-indigo-500"
            v-for="project in projects" :key="project.id" @mouseenter="toggleDescription(project)"
            @mouseleave="toggleDescription(project)">
            <div class="rounded h-1/2">
                <div class="h-full w-full">
                    <img :src="project.image" class="projectImage h-full w-full object-cover rounded-md" alt="Description">

                    <Transition name="slide-fade">
                        <p v-if="project.showDescription"
                            class="description font-bold text-white bg-indigo-400 m-auto py-4">
                            {{ project.description }}
                        </p>
                    </Transition>
                </div>
            </div>

            <div class="flex flex-col">
                <h3 class="text-2xl text-black underline self-center m-4">{{ project.title }}</h3>
                <div class="flex gap-4 self-center">
                    <div class="text-sm text-gray-500 " v-for="stack in project.techstack">
                        <div class="bg-indigo-300 border border-gray-500 rounded p-2 m-2 ">{{ stack }}</div>
                    </div>
                </div>
            </div>
            <div class="flex self-center justify-center items-center">
                <button
                    class="flex justify-center items-center gap-4 mt-4 mr-4 px-6 py-2 h-12 bg-indigo-500 rounded text-white font-bold">
                    <img src="github-mark-white.png" class="w-10 h-10"> Github
                </button>
                <button class="mt-4 px-6 py-2 h-12 bg-indigo-500 rounded text-white font-bold">Test it!</button>
            </div>
        </div>
    </div>
</template>
  
<script setup>
import { ref } from 'vue';

const projectHeader = "MeineProjekte".split("");
const projects = ref([
    {
        id: 1,
        title: "Memorily",
        description: "Ein effizientes CRUD-System, das den Nutzern ermöglicht, Notizen dynamisch zu erstellen, aktualisieren, lesen und löschen. Entwickelt mit Laravel und optimiert mit PaperCSS für eine reibungslose Benutzererfahrung. Backend-Datenpersistenz wurde mit einer MySQL-Datenbank realisiert.",
        image: "memorily.jpeg",
        techstack: ["Laravel", "PaperCSS", "MySQL"],
        showDescription: false
    },
    {
        id: 2,
        title: "ProspektCreator",
        description: "Eine interaktive Webanwendung, die CSV-Uploads für die Prospekterstellung unterstützt. Die Drag-and-Drop-Funktionalität bietet eine intuitive Benutzeroberfläche zur Prospektgestaltung. Integrierte Features erlauben es den Nutzern, per Klick auf Produkte eine Einkaufsliste zu generieren.",
        image: "prospektcreator.jpeg",
        techstack: ["Laravel", "VueJS", "Inertia", "MySQL", "tailwindCSS"],
        showDescription: false
    },
    {
        id: 3,
        title: "Catogram",
        description: "Ein Instagram-Klon, entwickelt sowohl als Single Page Application (SPA) mit Laravel, Vue und Inertia, als auch mit reinen Laravel Blade Views (und bisschen AlpineJS). Authentifizierung über GitHub wurde implementiert, zusammen mit einer Live-Kommentarfunktion über Pusher für Echtzeitinteraktionen. Infinite Scrolling sorgt für eine nahtlose Nutzererfahrung.",
        image: "catogram.jpeg",
        techstack: ["Laravel", "VueJS", "Inertia", "MySQL", "tailwindCSS"],
        showDescription: false
    },
]);

function toggleDescription(project) {
    const index = projects.value.findIndex(p => p.id === project.id);
    if (index !== -1) {
        projects.value[index].showDescription = !projects.value[index].showDescription;
        ;
    }
}
const startAnimation = (event) => {
    event.target.classList.add('jiggle-animation');
};

const endAnimation = (event) => {
    event.target.classList.remove('jiggle-animation');
};

</script>
  
<style scoped>
.hover-image {
    position: relative;
    overflow: hidden;
}

.hover-image:hover .projectImage {
    transform: translateY(-110%);
    transition: 0.5s;
}

.description {
    position: absolute;
    top: 20%;
    left: 0;
    text-align: center;
}

.slide-fade-enter-active {
    transition: all 0.6s ease-out 0.3s;
}

.slide-fade-leave-active {
    transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
    transform: translateY(-40px);
    opacity: 0;
}
</style>