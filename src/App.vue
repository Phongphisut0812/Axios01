<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/h3.png">    
    <!-- <HelloWorld msg="Welcome to Your Dictionary Search"/>  -->
    <h1>Welcome to Your Dictionary Search</h1>
    <anime />
  </div>
</template>

<script>
import Anime from'./components/Anime'

export default {
  name: 'App',
  components: {
    Anime
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
