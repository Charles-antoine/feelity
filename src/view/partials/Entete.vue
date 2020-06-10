<template>
  <div class="block block__header">
    <button class="button button-icon">     
      <img alt="back button" :src="back">
    </button>
    <a href="/" target="_self" class="icon">
      <img alt="feelity logo" :src="logo">
    </a>
  </div>
</template>

<script>
import { gsap, Sine } from 'gsap'

const timeline = gsap.timeline();
let $button;

export default {
  name: 'entete',
  props:[
    'loaded',
  ],
  data(){
    return {
        back : './assets/icon-arrow-back.svg',
        logo : './assets/feelity.svg',
    }
  },
  watch:{
    loaded(){
      this.animeIn();
    }
  },
  mounted() {
    $button = document.querySelector('.button-icon')    
    timeline.set($button, { opacity:0, x:10})
  },
  methods: {
    animeIn(){
      timeline.to($button, { duration:1, opacity:1, x:0, ease: Sine.easeInOut, delay:0})
    }
  }
}
</script>
