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
    <Footer />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld'
import Header from './components/Header'
import Shotchart from './components/Shotchart'
import Scoring from './components/Scoring'
import PlayByPlay from './components/PlayByPlay'
import Stats from './components/Stats'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    Header,
    Shotchart, 
    Scoring, 
    PlayByPlay,
    Stats,
    Footer
  }
}
</script>

<style lang="scss">
@import "styles/colors.scss";

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

 @media (max-width: 641px) {
  .content {
    padding-left: 5%;
    padding-right: 5%;
  }

  .primary-nav {
    display: none;
  }

  .logo-container {
    padding-left: 30%;
  }

  .content,
  .inside-left{
    flex-direction: column;
  }

}


</style>
