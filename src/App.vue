<template>
  <div id="app">
    <!-- <HelloWorld/> -->
    <Header />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld'
import Header from './components/Header'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    Header
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
