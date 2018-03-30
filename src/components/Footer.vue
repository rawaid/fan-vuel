<template>
<footer class="global-footer">
  <div class="global-footer__leagueRow">
    <span class="global-footer__league current">NBA</span>
    <span class="global-footer__league other">MLB</span>
    <span class="global-footer__league other">NCAAF</span>
  </div>
  <div class="global-footer__container">

      <span class="global-footer__left"><i class="fas fa-angle-left"></i></span>

      <div class="global-footer__currentGame">
          <div class="global-footer__teams">
              <div class="global-footer__team">Warriors</div>
              <div class="global-footer__team">Thunder</div>
              <span class="global-footer__time">7:34 4th - TV: ESPN</span>
            </div>
            
            <div class="global-footer__score">
                <span class="global-footer__points">96</span>
                <span class="global-footer__points">81</span>
            </div>
      
            <span class="global-footer__teamAbbr">GSW</span>
      
            <div class="global-footer__players">
              <div class="global-footer__away">
                  <span class="global-footer__player">S. Curry, PG</span>
                  <span class="global-footer__stats">23 points, 6 assists</span>
              </div>
            </div>
      
            <span class="global-footer__teamAbbr">OKC</span>
      
            <div class="global-footer__players">
              <div class="global-footer__home">
                  <span class="global-footer__player">K. Durant, SF</span>
                  <span class="global-footer__stats">30 points, 9 rebounds</span>
              </div>
            </div>
      </div>
     

        <div class="global-footer__otherGames">
          <div class="global-footer__otherTeams">
              <div class="global-footer__team">CHI</div>
              <div class="global-footer__team">BOS</div>
              <span class="global-footer__time">6:33 3rd</span>
          </div>

          <div class="global-footer__otherScore">
              <span class="global-footer__points">56</span>
              <span class="global-footer__points">54</span>
          </div>

          <div class="global-footer__otherTeams">
              <div class="global-footer__team">ATL</div>
              <div class="global-footer__team">MEM</div>
              <span class="global-footer__time">12:00 2nd</span>
          </div>

          <div class="global-footer__otherScore">
              <span class="global-footer__points">26</span>
              <span class="global-footer__points">24</span>
          </div>

        </div>
      <span class="global-footer__right"><i class="fas fa-angle-right"></i></span>

  </div>
</footer>

</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios, axios)

Vue.axios.get("https://my-json-server.typicode.com/fanduel/moneyball-fe-challenge-data/plays").then((response) => {
  console.log(response.data)
})

export default {
  name: 'Footer',
  data () {
    return {
      msg: 'ur header'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

$fanduel-navy: #2d363c;
$fanduel-bg: #bcbcbc;
$fanduel-highlight: #505a61;
$warriors: #fdb92c;
$thunder: #127dc2;
$container-header: #000000;
$white: #fff;
$border: #e5e5e5;
$spacer: #f2f2f2;
$light-gray: #cccccc;
$fd-gray: #333333;
$satan-gray: #666666;
$highlight: #fff8ea;
$selected-green: #669933;
$footer-gray: #505961;
$footer-current: #616a71;
$location-gray: #858585;
$other-games: #a8acb0;

.global-footer {
  position: sticky;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  height: 101px;
  background: $footer-gray;
  overflow-x: scroll;
  color: $white;
  -webkit-font-smoothing: antialiased;
  font-size: 0.875rem;

  &__leagueRow {
    background: $fanduel-navy;
    height: 22px;
    padding-left: 27px;
    padding-top: 5px;
    width: 120%;
  }

  &__league {
    padding: 5px 120px 6px 15px;
  }

  .current {
    background: $selected-green;
    font-weight: bold;
  }

  .other {
    color: $fanduel-highlight;
    border-right: 1px solid $fanduel-highlight;
  }


  &__left,
  &__right {
    padding: 27px 10px 27px 10px;
    background: $footer-gray;
  }

  &__right {
    margin-left: auto;
  }

  &__currentGame,
  &__otherGames{
    display: flex;
  }

  &__currentGame {
    background-color: $footer-current;
    padding: 11px 50px 11px 15px;
  }

  &__otherGames {
    color: $other-games;
  }

  &__otherScore {
    padding-right:20px;
    border-right: 1px solid $other-games;
    padding-top: 11px;
  }

  &__otherTeams {
    padding-left: 10px;
    padding-top: 11px;
  }

  &__teamAbbr {
    margin-left: 30px;
    padding-right: 5px;
    font-size: 11px;
    font-weight: bold;
  }

  &__team {
    padding: 1px;
    text-transform: uppercase;
  }

  &__points {
    font-weight: bold;
    margin-left: 20px;
    display: block;
  }

  &__time,
  &__stats {
    white-space: nowrap;
    font-size: 11px;
  }

  &__players {
    padding-left: 20px;
  }

  &__player {
    font-weight: bold;
  }

  &__away, 
  &__home {
    display: inline;
  }

  &__player {
    display: block;
  }

  &__container {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    max-width: 100%;
    margin: 0 auto;
  }
}

</style>
