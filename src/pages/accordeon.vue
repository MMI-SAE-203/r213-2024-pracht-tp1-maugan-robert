<script setup lang="ts">
import { ref } from "vue";
import { onErrorCaptured } from 'vue'
import { RouterLink, RouterView } from 'vue-router/auto'

onErrorCaptured((err, instance, info) => {
  console.error('erreur : ', err, '\ninfo : ', info, '\ncomposant : ', instance)
  return true
})
//
const sectionOpen = ref(1)
const sectionsData = [
  {
    label: 'bouton 1',
    texte: `texte panneau 1 Lorem ipsum dolor sit ame
    consectetur adipisicing elit. Inventore animi dolore,
    rerum magni laudantium quod excepturi laboriosam, 
    ex modi debitis harum reprehenderit eaque quam ut
    ea molestiae. Id, cum dolor!`
  },
  {
    label: 'bouton 2',
    texte: `texte panneau 2 Amet alias provident quos quis, 
    Officia ut ab dolores quos dolorem accusamus ad,
    consectetur unde minima, ipsum eligendi inventore id
    labore, laborum rerum laboriosam corrupti iste.
    Distinctio, perspiciatis!`
  },
  {
    label: 'bouton 3',
    texte: `texte panneau 3 Repudiandae corporis voluptates, 
    odit reprehenderit sint pariatur at voluptatum, cumque
    quia sit eligendi ex culpa eos, alias magnam molestiae
    id modi accusantium ipsa eveniet accusamus. Tempora 
    quis corporis et nam.`
  }
]
</script>

<template>
  <h1 class="text-2xl">Bonjour monde !</h1>

<section>
  <button class="text-xl" @pointerdown="sectionOpen = 1">bouton 1</button>
  <p v-show="sectionOpen == 1">loren...</p>
</section>

<section>
  <button class="text-xl" @pointerdown="sectionOpen = 2">bouton 2</button>
  <p v-show="sectionOpen == 2">loren...</p>
</section>

<section>
  <button class="text-xl" @pointerdown="sectionOpen = 3">bouton 3</button>
  <p v-show="sectionOpen == 3">loren...</p>
</section>

<section v-for="({ label, texte }, key) of sectionsData" :key="key">
  <pre class="font-mono">key : {{ key }}</pre>
  <pre class="font-mono">label : {{ label }}</pre>
  <pre class="font-mono">texte : {{ texte }}</pre>
</section>

</template>
