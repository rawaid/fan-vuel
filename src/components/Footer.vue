<template>
<footer class="global-footer">
  <div class="global-footer__leagueRow">
    <span class="global-footer__league current">NBA</span>
    <span class="global-footer__league other">MLB</span>
    <span class="global-footer__league other">NCAAF</span>
  </div>
  <div class="global-footer__container">

      <span class="global-footer__left"><i class="fas fa-angle-left"></i></span>

      <div class="global-footer__currentGame" v-for="game in scoreboard" v-bind:key="game.quarter">
          <div class="global-footer__teams">
              <div class="global-footer__team">{{ game.away_team.abbrev }}</div>
              <div class="global-footer__team">{{ game.home_team.abbrev }}</div>
              <span class="global-footer__time">{{ game.time_left }}</span>
            </div>
            
            <div class="global-footer__score">
                <span class="global-footer__points">{{ game.away_team.score }}</span>
                <span class="global-footer__points">{{ game.home_team.score }}</span>
            </div>
      
            <span class="global-footer__teamAbbr">{{ game.top_performers[0].team }}</span>
      
            <div class="global-footer__players">
              <div class="global-footer__away">
                  <span class="global-footer__player">{{ game.top_performers[0].name }}, {{ game.top_performers[0].position }}</span>
                  <span class="global-footer__stats">{{ game.top_performers[0].points }} points, {{ game.top_performers[0].rebounds }} rebounds</span>
              </div>
            </div>
      
            <span class="global-footer__teamAbbr">{{ game.top_performers[1].team }}</span>
      
            <div class="global-footer__players">
              <div class="global-footer__home">
                   <span class="global-footer__player">{{ game.top_performers[1].name }}, {{ game.top_performers[1].position }}</span>
                  <span class="global-footer__stats">{{ game.top_performers[1].points }} points, {{ game.top_performers[1].rebounds }} rebounds</span>
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

export default {
  name: 'Header',
  data () {
    return {
      scoreboard: [],
      dataLoaded: false
    }
  }, 
  mounted() {
    Vue.axios.get("https://my-json-server.typicode.com/fanduel/moneyball-fe-challenge-data/footer_scoreboard").then((response) => {
      this.dataLoaded = true;
      this.scoreboard = response.data;
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import "../styles/colors.scss";

.global-footer {
  position: sticky;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  height: 101px;
  background: $footer-gray;
  overflow-y: hidden;
  overflow-x: scroll;
  color: $white;
  -webkit-font-smoothing: antialiased;
  font-size: 0.875rem;

  &__leagueRow {
    background: $fanduel-navy;
    height: 22px;
    padding-left: 27px;
    padding-top: 5px;
    width: 100%;
  }

  &__league {
    padding: 5px 116px 6px 15px;
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
    padding: 11px 48px 11px 15px;
    border-right: 1px solid $other-games;
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
