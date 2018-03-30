<template>

    <div class="shotchart-container"  v-if="dataLoaded">
      <div class="shotchart-container__header">
        <div class="shotchart-container__header--away">
          <span class="shotchart-container__awayCity">{{ shotchart.away_team.location }} </span>
          <span class="shotchart-container__awayTeam">{{ shotchart.away_team.name }} </span>
        </div>

        <div class="shotchart-container__awayScore">{{ shotchart.away_team.score }}</div>

        <div class="shotchart-container__header--info">
          <span class="shotchart-container__header--time">{{ shotchart.time_left }} {{ shotchart.quarter }}th</span>
          <span class="shotchart-container__header--location">{{ shotchart.arena }}</span>
          <span class="shotchart-container__header--location">{{ shotchart.location }}</span>
        </div>

        <div class="shotchart-container__homeScore">{{ shotchart.home_team.score }}</div>

        <div class="shotchart-container__header--home">
            <span class="shotchart-container__homeCity">{{ shotchart.home_team.location }}</span>
            <span class="shotchart-container__homeTeam">{{ shotchart.home_team.name }}</span>
        </div>
      </div>

      <div class="shotchart-container__spacer">
        Last Play: TV Timeout. Go get a snack.
      </div>

      <div class="shotchart-container__content">
        <div class="shotchart-container__toggle">
          Show: <span class="shotchart-container__toggle--selected">Recent Shots <i class="fas fa-angle-down"></i></span>
        </div>

        <div class="shotchart-container__bottom">
          <div class="shotchart-container__awayStats">
            <ul v-for="shot in shotchart.away_team.shooting_stats">
              <li class="shotchart-container__statType">{{shot.title}}</li>
              <li class="shotchart-container__stat--away">{{shot.perc}}</li>
            </ul>
          </div>

          <div class="shotchart-container__shotchart">
            <img src="../assets/shotchart.png" alt="Warriors vs Thunder Shotchart"/>
          </div>

          <div class="shotchart-container__homeStats">
          <ul class="shotchart-container__homeStats" v-for="shot in shotchart.home_team.shooting_stats">
            <li class="shotchart-container__statType">{{shot.title}}</li>
            <li class="shotchart-container__stat--home">{{shot.perc}}</li>
          </ul>
          </div>
        </div>

      </div>

</div>

</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios, axios)

export default {
  name: 'Shotchart',
  data () {
    return {
      shotchart: [],
      dataLoaded: false
    }
  }, 
  mounted() {
    Vue.axios.get("https://my-json-server.typicode.com/fanduel/moneyball-fe-challenge-data/game_stats").then((response) => {
      this.dataLoaded = true;
      this.shotchart = response.data;
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import "../styles/colors.scss";

 .shotchart-container {
   margin: 5px;
   height: 450px;
   background: $white;
   border-radius: 10px;

   &__header {
     padding: 25px;
     display: flex;
     flex-direction: row;

     &--away {
      flex: 2;
      color: $warriors;
      text-align: left;
     }

     &--home {
      flex: 2;
      color:$thunder;
      text-align: right;
     }

     &--location {
      color: $location-gray;
      font-size: 11px;
     }

     &--time {
       padding-bottom: 5px;
       font-size: 13px;
     }

     &--info {
       flex: 1;
     }

     &--location,
     &--time {
       font-weight: bold;
       display: block;
       text-align: center;
       border-left: 1px solid $light-gray;
       border-right: 1px solid $light-gray;
       padding-left: 15px;
       padding-right: 15px;
     }
   }

   &__awayScore {
    color: $warriors;
    flex: 1;
  }

  &__homeScore {
    color: $thunder;
    flex: 1;
    text-align: right;
  }

  &__awayScore, 
  &__homeScore {
    flex: 1;
    font-size: 64px;
    font-weight: bold;
  }

   &__awayCity,
   &__awayTeam,
   &__homeCity,
   &__homeTeam {
     font-size: 20px;
     line-height: 20px;
     text-transform: uppercase;
   }

   &__awayCity,
   &__homeCity {
     font-weight: 400;
   }

   &__awayTeam,
   &__homeTeam {
     font-weight: bold;
     display: block;
   }

   &__spacer {
     background: $spacer;
     padding: 7px;
     display: block;
     text-transform: uppercase;
     font-size: 10px;
     text-align: center;
   }

   &__toggle {
     text-align: center;
     text-transform: uppercase;
     font-size: 12px;
     padding: 7px;

     &--selected {
       font-weight: bold;
     }
   }

   &__content {
     text-align: center;
   }

   &__bottom {
     display: flex;
   }

   &__awayStats,
   &__homeStats{
    list-style-type: none;
    display: inline-flex;
    flex-direction: column;
   }

   &__awayStats,
   &__homeStats,
   &__shotchart {
     flex: 3;
   }

   &__awayStats{
     position: relative;
 
   }

   &__statType {
     display: block;
     padding-bottom: 5px;
   }

   &__stat {
    display: inline;
    &--away,
    &--home {
      list-style-type: none;
      font-weight: 500;
      font-size: 24px;
      line-height: 22px;
      position: relative;
      &:after {
        content:""; 
        background: $light-gray; 
        position: absolute; 
        bottom: -10px; 
        margin-left: -80px;
        width: 90px; 
        height: 1px;
      }
    }


     &--away {
      color: $warriors;
     }

     &--home {
      color: $thunder;
     }
   }

 }

 @media (max-width: 641px) {
  .shotchart-container__header {
    flex-direction: column;
  }

  .shotchart-container {
    height: 100%;
    &__awayStats ul {
      padding: 0;
    }
    &__awayStats,
    &__homeStats{
      list-style-type: none;
      display: inline;
    }
    &__bottom {
      display: block;
    }
    &__content img {
      padding: 10px;
      width: 80%;
    }
    &__stat {
      &--away,
      &--home {

      &:after {
        content:""; 
        height: 0;
        }
      }
    }
  &__header {
    &--time,
    &--location {
      border: none;
    }
  }

  }
}
</style>
