<template>
  <div class="block__main" :class="{overflow : isLoading}">
      <loader v-if="isLoading" v-on:loaded="loadingDone"></loader>
      <entete :loaded="isLoading"></entete>
      <servicesContainer :loaded="isLoading"></servicesContainer>
      <articlesContainer  :loaded="isLoading" :delay="1.5"></articlesContainer>
  </div>
</template>

<script>
import servicesContainer from '../layouts/ServicesContainer'
import articlesContainer from '../layouts/ArticlesContainer'
import entete from '../partials/Entete'
import loader from '../components/Loader'
//
export default {
  name: 'home',
  components:{
      'loader'                : loader,
      'entete'                : entete,
      'servicesContainer'     : servicesContainer,
      'articlesContainer'     : articlesContainer,
  },
  data () {
    return {
      isLoading: true,
    }
  },
  methods: {
    loadingDone (){
      this.isLoading = !this.isLoading;
    }
  }
}
</script>