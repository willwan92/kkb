<template>
  <div id="app">
    <FormDemo/>
  </div>
</template>

<script>
import FormDemo from './components/FormDemo.vue'

export default {
  name: 'app',
  components: {
    FormDemo
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
