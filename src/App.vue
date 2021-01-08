<template>
  <div id="app">
    <TextSearch />
  </div>
</template>

<script>
import TextSearch from './components/TextSearch'

export default {
  name: 'App',
  components: {
    TextSearch
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
