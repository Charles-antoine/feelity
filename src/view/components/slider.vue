<template>
  <div class="block__slider">
    <VueSlickCarousel v-bind="settings">
      <div class="wrapper" v-for="(img,index) in images" :key="index">
          <img alt="describe image" :src="img.url">
      </div>
    </VueSlickCarousel>
  </div>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'
import { TimelineMax, Sine } from 'gsap'

const timeline = new TimelineMax({onComplete:() => {}})
let $wrapper;

export default {
  name: 'slider',
  components:{
      'VueSlickCarousel' : VueSlickCarousel,
  },
  props: [
    'loaded',
    'delay'
  ],
  data () {
    return {
        images: [
          {url : './assets/slider/Rectangle-9.png'},
          {url : './assets/slider/Rectangle-10.png'},
          {url : './assets/slider/Rectangle-9.png'},
          ],
        settings: {
            "focusOnSelect": true,
            "infinite": false,
            "slidesToShow": 1,
            "variableWidth": true,
            "speed": 500,
            "initialSlide": 0,          
            "responsive": [
                        {
                          "breakpoint": 2400,
                          "settings": {
                            "centerMode": true,
                            "slidesToShow": 1,
                            "slidesToScroll": 3,
                            "initialSlide": 1,
                          }
                        },
                        {
                          "breakpoint": 1023,
                          "settings": {
                            "centerMode": false,
                            "slidesToShow": 1,
                            "initialSlide": 0,
                            "slidesToScroll": 1,
                          }
                        }
                      ]
        }
    }
  },
  watch:{
    loaded(){
      this.animeIn();
    }
  },  
  mounted() {
    $wrapper = document.querySelectorAll('.wrapper')    
    timeline.set($wrapper, { opacity:0,x:30})
  }, 
  methods: {
    animeIn(){
      timeline.staggerTo($wrapper, .5, { opacity:1,x:0, ease: Sine.easeOut, delay:this.delay},0.3)
    }
  }   
}
</script>