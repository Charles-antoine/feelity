<template>
  <div class="block__services">
      <h1  class="block white title">{{title}}</h1>
      <slider :loaded="loaded" :delay='.25'></slider>
  </div>
</template>

<script>
import slider from '../components/Slider'
import { TimelineMax, Sine } from 'gsap'

const timeline = new TimelineMax({onComplete:() => {}})
let $title;

export default {
  name: 'servicesContainer',
  components:{
      'slider': slider,
  },
  props:[
    'loaded',
  ],
  data(){
    return {
      title: "Services"
    }
  },  
  watch:{
    loaded(){
      this.animeIn();
    }
  },
  mounted() {
    $title = document.querySelector('.title')    
    timeline.set($title, { opacity:0, y:30})
  },
  methods: {
    animeIn(){
      timeline.to($title, .5, { opacity:1, y:0, ease: Sine.easeOut, delay:0})
    }
  },
}
</script>