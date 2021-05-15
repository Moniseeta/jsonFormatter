<template>
  <JsonFormatter msg="Welcome to JsonFormatter App"/>
</template>

<script>
import JsonFormatter from './components/JsonFormatter.vue'

export default {
  name: 'App',
  components: {
    JsonFormatter
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
