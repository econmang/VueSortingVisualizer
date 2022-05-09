<template>
  <h1>Sorting Algorithm Visualization</h1>
  <VisualSorter />
</template>

<script>
import VisualSorter from './components/VisualSorter.vue'

export default {
  name: 'App',
  components: {
    VisualSorter
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
