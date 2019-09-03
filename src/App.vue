<template>
  <div id="app">
    <!-- <redBG/> -->
    <redBag/>
  </div>
</template>

<script>
import redBag from './components/redBag.vue'
// import redBG from './components/redBG.vue'

export default {
  name: 'app',
  components: {
    redBag,
    // redBG
  }
}
</script>
<style lang='scss' scoped>
@import url('../styles/stylesheets/screen.css');
</style>
