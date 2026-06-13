<template>
  <!--
  <img alt="Vue logo" src="./assets/logo.png">
  
  <HelloWorld msg="Welcome to Your Vue.js App"/>-->
  <ThreeD1></ThreeD1>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import ThreeD1 from './components/ThreeD1.vue';
export default {
  name: 'App',
  components: {
    ThreeD1
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
h1{
  font-size: 10px;
}
</style>
