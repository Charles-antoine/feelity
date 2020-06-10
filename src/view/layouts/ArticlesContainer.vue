<template>
  <div class="block block__articles">
    <div class="left show-for-medium" ref="img">
        <img alt="describe image" :src="'./assets/slider/Rectangle-10.png'">
    </div>
    <div class="right">
      <h1 class="black" ref="title">{{title}}</h1>
      <p class="desc" ref="desc">{{desc}}</p>
      <a href="#" target-="_self" class="button-full" ref="btFull">
          <span>{{label}}</span>
          <button class="button button-icon reverse">     
            <img alt="back button" :src="url">
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
      title : 'Articles',
      desc : 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas sit amet malesuada ex, consectetur convallis erat. Sed viverra id metus in eleifend. ',
      'label' : 'Commencer à lire', 
      'url' :'./assets/icon-arrow-next.svg'
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