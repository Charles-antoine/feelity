<template>
  <home></home>
</template>
<script>

import home from './layouts/Home'

export default {
  name: 'Main',
  components:{
    home,
  },
  props: {
    msg: String
  },
  data () {
    return {
    }
  }
}
</script>

<style scoped>
</style>
