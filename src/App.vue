<template>
  <div id="app">
    <!-- <HelloWorld/> -->
    <Header />
    <div class="content">
      <div class="left-container">
        <Shotchart />
        <div class="inside-left">
          <PlayByPlay />
          <Stats />
        </div>
      </div>
      <Scoring />
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld'
import Header from './components/Header'
import Shotchart from './components/Shotchart'
import Scoring from './components/Scoring'
import PlayByPlay from './components/PlayByPlay'
import Stats from './components/Stats'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    Header,
    Shotchart, 
    Scoring, 
    PlayByPlay,
    Stats
  }
}
</script>

<style lang="scss">
$fanduel-bg: #bcbcbc;

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 100%;
  height: 100%;
  margin: 0;
  background: $fanduel-bg;

}

 .content {
   display: flex;
   margin-top: 60px;
   padding: 20px;
 }

.left-container {
   flex: 3;
 }

  .inside-left {
  display: flex;
 }


</style>
