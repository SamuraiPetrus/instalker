<template>
  <div id="app">
      <Home></Home>
      <User></User>
  </div>
</template>

<script>

import Home from './components/Home.vue'
import User from './components/User/User.vue'
export default {
  name: 'App',
  components: {
      Home,
      User
  }
}
</script>

<style>
#app {
    min-height: 100vh;
}
</style>
