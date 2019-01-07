<template lang="pug">
  #app
    video#videobcg(preload='auto', autoplay='true', loop='loop', muted='muted', volume='0')
      source(src='./assets/smoke.mp4', type='video/webm')
      |           Sorry, your browser does not support HTML5 video.
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
#videobcg 
  position fixed
  top 0
  left 0
  width 100%
  min-width 200%
  z-index -1
  pointer-events none
  overflow hidden
</style>
