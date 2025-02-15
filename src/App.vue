<template>
  <ToggleView />
  <HelloWorld msg/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import ToggleView from './components/toggleView.vue';

export default {
  name: 'App',
  components: {
    HelloWorld, ToggleView
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
