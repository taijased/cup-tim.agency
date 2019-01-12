<template lang="pug">
  #app
    Index
</template>

<script>
import Index from './components/Index.vue'

export default {
  name: 'app',
  components: {
    Index
  }
}
</script>
<style lang="stylus">
body 
  margin 0
  padding 0
#app
  font-family 'TT Norms Regular', Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  overflow hidden
</style>
