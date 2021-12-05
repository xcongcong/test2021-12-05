<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Search/>
    <Userlist/>
  </div>
</template>

<script>
import Search from './components/Search.vue'
import Userlist from './components/Userlist.vue'

export default {
  name: 'App',
  components: {
    Search,
    Userlist
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
