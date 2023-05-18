<template>
  <!-- <HelloWorld /> -->
  <!-- <CounterComponent /> -->
  <MyApp />
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import MyApp from './components/MyApp.vue';
// import CounterComponent from './components/CounterComponent.vue'


export default {
  name: 'App',
  components: {
    // HelloWorld
    // CounterComponent 
    MyApp

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
