<template>
  <div id="app">
    <h1>Quiz App</h1>
    <quiz/>
  </div>
</template>

<script>
import Quiz from './components/Quiz.vue'

export default {
  components: { Quiz },
  name: 'App',
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  line-height: 1.6;
}
</style>
