<template>
  <div class="block__loader">
          <div class="back" ref="back"></div>
          <div class="logo" ref="logo">
            <img alt="feelity logo" :src="'./assets/feelity.svg'">
          </div>
  </div>
</template>

<script>
import { TimelineLite, Sine, Circ } from 'gsap'


export default {
  name: 'loader',
  mounted() { 
    const { logo, back } = this.$refs
    const timeline = new TimelineLite({onComplete:() => {this.loaded();}})
    timeline.to(logo, .5, { opacity: 1,top:"50%", ease: Sine.easeOut, delay:0.5}) 
    timeline.to(back, 1, { top: "100%", ease: Circ.easeInOut, delay:.75})
    timeline.to(logo, 1, { opacity: 0,top:"90%", ease: Circ.easeInOut, delay:-.95}) 
  },
  methods: {
    loaded () {
      const $block = document.querySelector('.block__loader');
      $block.style.display = 'none';
      this.$emit('loaded');
    }
  }, 
}
</script>