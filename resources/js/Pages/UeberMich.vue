<template>
    <container class="w-full flex flex-col justify-center items-center">

        <Head title="Über mich" />
        <div class="flex mt-[150px] p-4 justify-center">
            <header v-for="char in ueberMichHeader" :key="char" class="text-6xl shadow-md shadow-indigo-600 flex mx-2 p-4"
                v-intersection-observer="onIntersectionObserver" @mouseover="startAnimation" @animationend="endAnimation">
                {{ char }}
            </header>
        </div>
        <div
            class="flex flex-col justify-around lg:w-1/2 my-10 p-3 rounded-3xl text-gray-800 font-bold shadow-xl shadow-indigo-500">
            <div class=" mt-4 p-8">

                <Transition name="slide-fade">

                    <p v-show="isVisible">
                        Anfang des Jahres war ich in der PHP-Welt noch ein Frischling, da mein Fokus zuvor auf der
                        Frontend-Entwicklung
                        lag.
                        Doch als ich mich intensiver damit auseinandersetzte, zogen mich insbesondere die Kombination von
                        Laravel,
                        Vue.js und Tailwind CSS in ihren Bann.
                        Während ich grundsätzlich allen Technologien aufgeschlossen gegenüberstehe, wäre es für mich eine
                        besondere
                        Freude, mit diesem Stack zu arbeiten.
                    </p>

                </Transition>

                <Transition name="slide-fade">

                    <p v-if="isVisible">
                        Dank meiner schnellen Auffassungsgabe (und vielleicht auch einer Extra-Portion Koffein) habe ich in
                        nur
                        wenigen
                        Monaten
                        den Sprung von "PHP-was?" zu "Laravel-ist-genial" geschafft. Dieses Engagement mündete in einer
                        Weiterbildung
                        zum PHP- und Laravelentwickler,
                        die ich mit der Note "sehr gut (1,3)" abschloss.
                    </p>

                </Transition>

                <Transition name="slide-fade">
                    <p v-if="isVisible">
                        Abseits der Programmierwelt bin ich ein leidenschaftlicher Gamer, Katzendaddy und eingefleischter
                        Fußballfan.
                        Ab und zu mal Joggen, Fitnesstraining oder ein gutes Buch, helfen mir, den Kopf frei zu bekommen.
                    </p>
                </Transition>

                <Transition name="slide-fade">
                    <p v-if="isVisible"> Und wie ist es mit mir zusammen zu arbeiten? Nun, abseits von Code und Controllern
                        (die
                        in
                        meinen Händen
                        natürlich) bin
                        ich auch ein angenehmer Geselle.
                        Neben einer professionellen Arbeitsweise, versuche ich den Spaß bei der Arbeit nicht zu kurz kommen
                        zu
                        lassen.
                    </p>
                </Transition>

                <Transition name="slide-fade">
                    <p v-if="isVisible">
                        Für mich steht die Loyalität dem Arbeitgeber gegenüber immer an oberster Stelle.
                        Ich bin nicht der Typ, der pünktlich um 17 Uhr den Stift fallen lässt.
                        Es treibt mich an, mich stetig zu verbessern und sicherzustellen, dass mein Arbeitgeber stolz darauf
                        ist,
                        mich
                        im Team zu haben.
                        Wenn dieser denkt "Das war ein Glücksgriff mit diesem Typen!", erst dann bin ich zufrieden.
                        Mein Fokus liegt stets auf der nächsten Herausforderung und darauf, den nächsten Schritt in Richtung
                        Erfolg
                        zu
                        gehen.
                        Und das nicht, weil ich muss, sondern weil ich es will.
                    </p>
                </Transition>

                <Transition name="slide-fade">
                    <p v-if="isVisible"> Und jetzt die Frage an Sie: Möchten Sie wirklich auf einen Mitarbeiter verzichten,
                        der
                        so
                        engagiert und
                        lernwillig ist? </p>
                </Transition>
            </div>
        </div>
    </container>
</template>
  
<script setup>

import { Head } from '@inertiajs/vue3';
import { vIntersectionObserver } from '@vueuse/components'
import { ref } from 'vue';
import { debounce } from 'lodash';

const ueberMichHeader = "MeineStory".split("");
const isVisible = ref(false);

const debouncedIntersectionObserver = debounce(([{ isIntersecting }]) => {
    isVisible.value = isIntersecting;
    console.log(isVisible.value);
}, 300);

function onIntersectionObserver(entries) {
    debouncedIntersectionObserver(entries);
}
const startAnimation = (event) => {
    event.target.classList.add('jiggle-animation');
};

const endAnimation = (event) => {
    event.target.classList.remove('jiggle-animation');
};
</script>
  
<style>
p {
    margin: 1rem 0;
}

.slide-fade-enter-active {
    transition: all 1.2s ease-in 0.75s;
}

.slide-fade-leave-active {
    transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
    transform: translateY(-80px);
    opacity: 0;
}

p:nth-child(n) {
    transition-delay: calc(n * 0.6s);
}</style>
