<template>
  <div class="pbp-container" v-if="dataLoaded">
    <div class="pbp-container__header">
      Play By Play
    </div>
    
    <div class="pbp-container__row" v-for="play in plays" v-bind:key="play.id">
      <div class="pbp-container__headshot">
        <img v-bind:src="'../static/' + play.scoring_player + '.png'"/>
      </div>
      <div class="pbp-container__content">
        <span class="pbp-container__time">
          {{ play.time_left }}
        </span>
        <div class="pbp-container__play">
          <div><span class="pbp-container__player">{{play.player}}</span> {{play.play}}</div>
        </div>
      </div>
      <span class="pbp-container__score">{{play.away_score}}-{{play.home_score}}, GS</span>
    </div>

    <!-- <div class="pbp-container__row">
      <div class="pbp-container__headshot">
        <img src="../img/Curry.png" alt="Stephen Curry"/>
      </div>
      <div class="pbp-container__content">
        <span class="pbp-container__time">
          7:34 4th
        </span>
        <div class="pbp-container__play">
          <div><span class="pbp-container__player">Stephen Curry</span> makes 13-foot jumper.</div>
          <div>Assisted by <span class="pbp-container__player">Draymond Green.</span></div>
        </div>
      </div>
      <span class="pbp-container__score">96-81, GS</span>
    </div> -->

  </div>
</template>


<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'


export default {
  name: 'PlayByPlay',
  data () {
    return {
      plays: [],
      dataLoaded: false
    }
  },
  mounted() {
    Vue.axios.get("https://my-json-server.typicode.com/fanduel/moneyball-fe-challenge-data/plays").then((response) => {
      this.dataLoaded = true;
      this.plays = response.data;

      function capitalize(value) {
        if (!value) return ''
        value = value.toString()
        return value.charAt(0).toUpperCase() + value.slice(1);
      }

      // string manipulation to for the bold player names   
      for (var x in this.plays) {
        this.scoringPlayer = this.plays[x].scoring_player.split("_");
        this.scoringPlayer = capitalize(this.scoringPlayer[0]) + " " + capitalize(this.scoringPlayer[1]);
        
        // "Steph Curry in the data feed as the scoring player but Stephen Curry in the description"
        if (this.scoringPlayer !== "Steph Curry") {
          this.play = this.plays[x].description.split(this.scoringPlayer);
        } 
        if (this.scoringPlayer == "Steph Curry") {
          this.play = this.plays[x].description.split("Stephen Curry");
        }
        this.plays[x].player = this.scoringPlayer;
        this.plays[x].play = this.play[1];
      }
    })
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

 .pbp-container {

   margin: 5px;
   background: $white;
   min-height: 427px;
   height: 100%;
   flex: 1;

    &__row {
     padding: 10px;
     display: flex;
     border-bottom: 1px solid $light-gray;
   }

   &__header{
    text-align: center;
    height: 15px;
    padding: 10px;
    text-transform: uppercase;
    font-size: 12px;
    font-weight: 600;
    line-height: 17px;
    letter-spacing: -0.24px;
    background: $container-header;
    color: $white;
   }

  .highlighted {
    background: linear-gradient(to top, $highlight, $white);
  }

  

   &__headshot {
     margin-right: 5px;
   }

   &__player,
   &__score {
     font-weight: bold;
   }

   &__player,
   &__play {
     line-height: 14px;
   }

   &__play {
     color: $fd-gray;
     font-size: 12px;
     font-weight: 500;
   }

   &__play div {
     display: block;
   }

   &__time {
     font-size: 11px;
     color: $satan-gray;
     font-weight: 500;
     letter-spacing: -0.22px;
   }

   &__score {
     flex: 2;
     padding-top: 3px;
     text-align: right;
     font-size: 14px;
     letter-spacing: -0.24px;
     align-content: center;
   }
 }

</style>
