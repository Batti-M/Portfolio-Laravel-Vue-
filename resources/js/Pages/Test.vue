<template>
    <div ref="container">
      <Head title="Über mich" />
      <h1 class="text-3xl"> Über mich </h1>
      <div class="flex flex-col justify-center w-1/2 font-bold mt-0 "  v-intersection-observer="onIntersectionObserver">
        <TransitionGroup>
          <Transition name="slide-fade" mode="out-in" appear v-for="(text, index) in texts" :key="index">
            <section v-show="isVisible">
              <p>{{ text }}</p>
            </section>
          </Transition>
        </TransitionGroup>
      </div>
    </div>
  </template>
  
  <script setup>
  import { Head } from '@inertiajs/vue3';
  import { Transition, TransitionGroup } from 'vue';
  import { vIntersectionObserver } from '@vueuse/components';
  import { ref } from 'vue';
  import { debounce } from 'lodash';
  
  const texts = [
    'Anfang des Jahres war ich in der PHP-Welt noch ein Frischling, da mein Fokus zuvor auf der Frontend-Entwicklung lag. Doch als ich mich intensiver damit auseinandersetzte, zogen mich insbesondere die Kombination von Laravel, Vue.js und Tailwind CSS in ihren Bann. Während ich grundsätzlich allen Technologien aufgeschlossen gegenüberstehe, wäre es für mich eine besondere Freude, mit diesem Stack zu arbeiten.',
    'Dank meiner schnellen Auffassungsgabe (und vielleicht auch einer Extra-Portion Koffein) habe ich in nur wenigen Monaten den Sprung von "PHP-was?" zu "Laravel-ist-genial" geschafft. Dieses Engagement mündete in einer Weiterbildung zum PHP- und Laravelentwickler, die ich mit der Note "sehr gut (1,3)" abschloss.',
    'Abseits der Programmierwelt bin ich ein leidenschaftlicher Gamer, Katzendaddy und eingefleischter Fußballfan. Ab und zu mal Joggen, Fitnesstraining oder ein gutes Buch, helfen mir, den Kopf frei zu bekommen.',
    'Und wie ist es mit mir zusammen zu arbeiten? Nun, abseits von Code und Controllern (die in meinen Händen natürlich) bin ich auch ein angenehmer Geselle. Neben einer professionellen Arbeitsweise, versuche ich den Spaß bei der Arbeit nicht zu kurz kommen zu lassen.',
    'Für mich steht die Loyalität dem Arbeitgeber gegenüber immer an oberster Stelle. Ich bin nicht der Typ, der pünktlich um 17 Uhr den Stift fallen lässt. Es treibt mich an, mich stetig zu verbessern und sicherzustellen, dass mein Arbeitgeber stolz darauf ist, mich im Team zu haben. Wenn dieser denkt "Das war ein Glücksgriff mit diesem Typen!", erst dann bin ich zufrieden. Mein Fokus liegt stets auf der nächsten Herausforderung und darauf, den nächsten Schritt in Richtung Erfolg zu gehen. Und das nicht, weil ich muss, sondern weil ich es will.',
    'Und jetzt die Frage an Sie: Möchten Sie wirklich auf einen Mitarbeiter verzichten, der so engagiert und lernwillig ist?'
  ];



const isVisible = ref(false);

const debouncedIntersectionObserver = debounce(([{ isIntersecting }]) => {
  isVisible.value = isIntersecting;
  console.log(isVisible.value);
}, 300);

function onIntersectionObserver(entries) {
  debouncedIntersectionObserver(entries);
}

  </script>
  
  <style>
  p {
    margin: 1rem 0;
  }
  
  .slide-fade-enter-active {
    transition: all 0.6s ease-out;
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