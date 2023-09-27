<template>
  <Head title="Über mich" />
  <div class="h-screen flex flex-col justify-center w-1/2 font-bold mt-0 ">
    <img src="/self_portrait.png" alt="portrait" class="reveal2 rounded-full w-[200px] h-[200px] self-end shadow-xl shadow-black">
    <div class="text-black">
      <template v-for="(char, index) in introduction">
        <span v-if="char !== ' '" :key="index" :class="index % 2 === 0 ? 'reveal1' : 'reveal2'" :style="`--i:${index};`"
          class="revealText">
          {{ char }}
        </span>
        <span v-else :key="char" :style="`--i:${index};`" class="revealText revealSpace">
          &nbsp;
        </span>
      </template>
    </div>
    <div class="flex">
      <div v-for="char in nameChars" :key="char" class="text-9xl shadow-md" @mouseover="startAnimation"
        @animationend="endAnimation">
        {{ char }}
      </div>
    </div>
    <div class="flex">
      <div v-for="char in surnameChars" :key="char" class="text-9xl shadow-md shadow-blue" @mouseover="startAnimation"
        @animationend="endAnimation">
        {{ char }}
      </div>
    </div>
    <div class="text-black mt-4">
      <template v-for="(char, index) in introduction2">
        <span v-if="char !== ' '" :key="index" :class="index % 2 === 0 ? 'reveal1' : 'reveal2'" :style="`--i:${index};`"
          class="revealText">
          {{ char }}
        </span>
        <span v-else :key="char" :style="`--i:${index};`" class="revealText revealSpace">
          &nbsp;
        </span>
      </template>
    </div>
    
    <a href="mailto:bartosz-m@outlook.de" class="mt-10">
      <button @mouseover="animate_paperplane = !animate_paperplane" class="border border-gray-800 rounded flex flex-col justify-center items-center p-2">
        <img src="paper-plane.svg" alt="paper-plane" :class="animate_paperplane ? 'paperplane_animation' : ''" class="w-12 h-12" />
        Get in touch with me
      </button>
    </a>

  </div>
</template>

<script setup>
import { ref } from 'vue';

const animate_paperplane = ref(false);

const name = "Bartosz";
const surname = "Mieszkalski";

const nameChars = name.split("");
const surnameChars = surname.split("");

const startAnimation = (event) => {
  event.target.classList.add('jiggle-animation');
};

const endAnimation = (event) => {
  event.target.classList.remove('jiggle-animation');
};

const introduction = "Hi, my name is".split("");
const introduction2 = "and I am a Full Stack web developer".split("");
</script>

<style >
@keyframes jiggle {
  0% {
    transform: scale(1);
  }

  25% {
    transform: scale(1.1);
  }

  50% {
    transform: scale(0.9);
  }

  75% {
    transform: scale(1.1);
  }

  100% {
    transform: scale(1);
    color: rgb(84, 16, 241);
    text-shadow: 11px 11px 21px rgb(0, 6, 8);
  }
}

.jiggle-animation {
  animation: jiggle 1.25s ease forwards;
}

.revealText {
  font-family: "Work Sans", sans-serif;
  font-weight: 900;
  opacity: 0;
}



@keyframes fadeInFromBottom {
  0% {
    opacity: 0;
    transform: translateY(100%);
  }

  70% {
    transform: translateY(-10%);
  }

  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeInFromTop {
  0% {
    opacity: 0;
    transform: translateY(-100%);
  }

  70% {
    transform: translateY(10%);
  }

  100% {
    opacity: 1;
    transform: translateY(0);
  }
}




.reveal1,
.reveal2 {
  display: inline-block;
}

.reveal1 {
  /* even letters */
  animation: fadeInFromBottom 0.5s ease-in forwards;
  animation-delay: calc(0.1s * var(--i));
}

.reveal2 {
  /* odd letters */
  animation: fadeInFromTop 1s ease-in forwards;
  animation-delay: calc(0.1s * var(--i));
}

.revealSpace {
  width: 2px;
  /* You can adjust the width as needed */
}

.paperplane_animation {
  animation: flyaway 2500ms forwards ease-in-out;
  transform: translateX(-50%) translateY(-50%) translate(0, 0) rotate(-15deg);
}

@keyframes flyaway {
  0% {
    transform: translateX(-20%) translateY(-20%) translate(0, 0) rotate(-15deg);
  }

  50% {
    transform: translateX(-50%) translateY(-50%) translate(500px, -100px) scale(0.5) rotate(-122deg);
    opacity: 0.5;
  }

  100% {
    transform: translateX(100%) translateY(-50%) translate(0, 0) scale(0) rotate(-120deg);
    opacity: 0;
  }
}
</style>


