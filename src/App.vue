<template>
  <div id="app">
    <Main/>
  </div>
</template>

<script>
import Main from './view/Main.vue'
import './css/style.scss';


export default {
  name: 'App',
  components: {
    Main
  }
}
</script>


<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
