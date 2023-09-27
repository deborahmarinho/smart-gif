<template>
  <img alt="Vue logo" src="./assets/logo.gif" height="100" width="130" style="max-width: 130px;">
  <GifHome msg="Gifs"/>
</template>

<script>
import GifHome from './components/GifHome.vue'

export default {
  name: 'App',
  components: {
    GifHome
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
