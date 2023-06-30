<template>
  <q-page padding class="bg-pink-1 flex justify-center fade-in">
    <div class="q-mt-xl" style="width: 30rem;">
      <div class="text-center">
        <!-- INPUT -->
        <div class="q-mb-md">
          <q-input dense v-model="text" clearable autofocus color="pink-12" label="jejemon k b?" clear-icon="close"
            @keydown.enter="jejenize" />
          <q-btn @click="jejenize" :disabled="!text" class="q-px-xl q-py-sm q-mt-md" color="pink" outline
            label="jejenize!" />
        </div>
        <!-- OUTPUT-->
        <div class="fade-in" v-if="jejenizedText">
          <q-input v-model="jejenizedText" outlined color="pink-12" type="textarea">
            <template v-slot:append>
              <q-btn @click="copy" round dense flat icon="fa-solid fa-clipboard" />
            </template>
          </q-input>
        </div>
        <!-- ABOUT PAGE -->
        <div class="fade-in" style="margin-top:200px;">
          <div>
            <div class="text-caption q-mb-md p">You may ask wtf is this? Well, this is a jejenator. It turns your text
              into
              jejemon.
              Wtf is jejemon? well.. <a href="https://en.wikipedia.org/wiki/Jejemon" target="_blank">jejemon</a>. Just
              click that link u
              uncultured swine.</div>
            <div class="text-caption q-mb-md p">This project was inspired from a fellow pinoy out there who made his own
              <a href="https://jejenator.netlify.app/" target="_blank">jejenator </a> website, shout out po sir Mark!
            </div>
            <div class="text-caption q-mb-md">I made this using <a class="text-green" href="https://vuejs.org/"
                target="_blank">vue.js </a>
            </div>
            <div class="text-caption q-mb-md p">Without my girlfriend, this website wouldn't be possible, thank you babe!
              I
              love you lalay my forever babie!!! (hence the pink theme).</div>
            <div class="text-caption">&copy; Made by N!țsvj @PmAc@lliV - 2023</div>
          </div>
        </div>
      </div>
    </div>
    <!-- dialog -->
    <q-dialog v-model="copied" seamless position="bottom">
      <q-card style="width: 350px">
        <q-linear-progress :value="1" color="pink-11" />
        <q-card-section class="text-center">
          <div>
            <div class="text-grey">Jejetext copied!</div>
          </div>
        </q-card-section>
      </q-card>
    </q-dialog>
  </q-page>
</template>

<script setup>
import { ref } from 'vue';

const text = ref('')
const jejenizedText = ref('')
const jejeLetters = {
  a: ['@', 'A', 4, 6],
  b: ['B', 8, 'ɓ'],
  c: ['C', 'c', 'ĉ',],
  d: ['d', 'D', 'cl',],
  e: ['e', 'E', 3, 'ë', '€'],
  f: ['f', 'F'],
  g: ['g', 'G', 'q', '&',],
  h: ['h', 'H', '#', 'j'],
  i: ['i', 'I', '!'],
  j: ['j', 'J'],
  k: ['k', 'K'],
  l: ['l', 'L', '£'],
  m: ['m', 'M'],
  n: ['ŋ', 'N', 'n', 'ň'],
  o: ['ø', 'o', 'O', 'ö', 'u'],
  p: ['p', 'P'],
  q: ['q', 'Q'],
  r: ['R', 'r', 'ř'],
  s: ['s', 'S', '$'],
  t: ['T', 't', 'ț', '+'],
  u: ['u', 'ü', 'U', 'v', 'o'],
  v: ['v', 'V'],
  w: ['w', 'W', 'vv', 'ẅ', '₩'],
  x: ['x', 'X', '×'],
  y: ['Y', 'y', 'ÿ', '¥'],
  z: ['z', 'Z', 'ž', 'x'],
  '!': ['!'],
  '?': ['?'],
  '@': ['@'],
  $: ['$'],
  0: [0],
  1: [1],
  2: [2],
  3: [3],
  4: [4],
  5: [5],
  6: [6],
  7: [7],
  8: [8],
  9: [9],
  ',': [','],
  '.': ['.'],
  '/': ['/'],
  '-': ['-']
};


const jejenize = () => {
  const words = text.value.split(' ');
  const randomizedWords = words.map((word) => {
    const characters = word.split('');
    const randomizedCharacters = characters.map((char) => {
      const letter = char.toLowerCase();
      const symbols = jejeLetters[letter];
      const randomIndex = Math.floor(Math.random() * symbols.length);
      return symbols[randomIndex];
    });
    return randomizedCharacters.join('');
  });
  jejenizedText.value = randomizedWords.join(' ');
}

const copy = () => {
  if (jejenizedText.value) {
    navigator.clipboard.writeText(jejenizedText.value)
      .then(() => {
        copied.value = true
        setTimeout(() => {
          copied.value = false;
        }, 1500)
      })
      .catch((error) => {
        console.error('Error copying text to clipboard:', error);
      });
  }
};
const copied = ref(false)


</script>

<style scoped></style>
