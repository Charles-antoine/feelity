<template>
  <div class="block__loader">
          <div class="back" ref="back"></div>
          <div class="logo" ref="logo">
            <img alt="feelity logo" :src="logo">
          </div>
  </div>
</template>

<script>
import { gsap, Sine, Circ } from 'gsap'


export default {
  name: 'loader',
  mounted() { 
    this.animeIn();
  },
  data(){
    return {
      logo: "./assets/feelity.svg"
    }
  },    
  methods: {
    loaded () {
      const $block = document.querySelector('.block__loader');
      $block.style.display = 'none';
      this.$emit('loaded');
    },
    animeIn () {
      const { logo, back } = this.$refs
      const timeline = gsap.timeline({onComplete:() => {this.loaded();}})
      timeline.to(logo, .5, {duration:.5, opacity: 1,top:"50%", ease: Sine.easeOut, delay:0.5}) 
      timeline.to(back, 1, {duration:1, top: "100%", ease: Circ.easeInOut, delay:.75})
      timeline.to(logo, 1, {duration:1, opacity: 0,y:"90", ease: Circ.easeInOut, delay:-.95}) 
    }
  }
}
</script>