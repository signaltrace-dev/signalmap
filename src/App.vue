<template>
  <div id="app">
      <mapwidget apikey="AIzaSyCnjHvBO9vjUQFI1s6P5dqcUnCozxB1HxQ"></mapwidget>
  </div>
</template>

<script>
import MapWidget from './components/Map.vue'

export default {
  name: 'app',
  components: {'mapwidget': MapWidget}
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
