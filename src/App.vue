<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Three_02></Three_02>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue';
import Three_01 from './components/three_01.vue'
import Three_02 from './components/three_02.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld
    Three_01,
    Three_02
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
