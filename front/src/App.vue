<template>
  <div id="app">
      <!-- <Home></Home> -->
      <User></User>
  </div>
</template>

<script>

// import Home from './components/Home.vue'
import User from './components/User.vue'
export default {
  name: 'App',
  components: {
      User
  }
}
</script>

<style>
#app {
    min-height: 100vh;
}
</style>
