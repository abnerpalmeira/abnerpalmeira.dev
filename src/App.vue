<template>
  <div id="app">
    <Animation/>
  </div>
</template>

<script>
import Animation from './components/Animation.vue'

export default {
  name: 'App',
  components: {
    Animation
  }
}
</script>

<style>

body{
  background-color:rgb(0,0,0);
  overflow: hidden;
  height: 100vh;
}
</style>
