<template>
  <div class="block block__articles">
    <div class="left show-for-medium" ref="img">
        <img alt="describe image" :src="urlImageDesktop">
    </div>
    <div class="right">
      <h1 class="black" ref="title">{{title}}</h1>
      <p class="desc" ref="desc">{{desc}}</p>
      <a :href="linkPortfolio" target="_blank" class="button-full" ref="btFull">
          <span>{{label}}</span>
          <button class="button button-icon reverse">     
            <img alt="back button" :src="urlButton">
          </button>
      </a>
    </div>
  </div>
</template>

<script>
import { gsap, Sine } from 'gsap'

const timeline = gsap.timeline({onComplete:() => {}})

export default {
  name: 'articlesContainer',
  props:[
    'loaded',
    'delay'
  ],
  data () {
    return {
      $elements: [],
      linkPortfolio: 'https://sinifikant.com',
      title : 'Articles',
      desc : 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas sit amet malesuada ex, consectetur convallis erat. Sed viverra id metus in eleifend. ',
      'label' : 'Commencer à lire', 
      'urlButton' :'./assets/icon-arrow-next.svg',
      'urlImageDesktop' :'./assets/slider/Rectangle-10.png'
    }
  },
  watch:{
    loaded(){
      this.animeIn();
    }
  },  
  mounted() {
    const { title, desc, btFull, img } = this.$refs;    
    this.$elements = [img,title,desc,btFull];
    timeline.set(this.$elements , { opacity:0, y:30})
  },  
  methods: {
    animeIn(){
      timeline.to(this.$elements,.5,{ opacity:1, y:0, ease: Sine.easeOut, delay:this.delay, stagger:.2},"<-1")
    }
  }  
}
</script>