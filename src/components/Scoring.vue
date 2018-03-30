/* eslint-disable */
<template>

  <div class="scoring-container">
    <div class="scoring-container__header">Your Scoring</div>
    <div class="scoring-container__nav">
    <span class="scoring-container__item scoringTab">This Game</span>
    <span class="scoring-container__item">All Games</span>
    </div>
  </div>

</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'


export default {
  name: 'Scoring',
  data () {
    return {
      msg: 'ur header'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import "../styles/colors.scss";

.scoring-container {
   margin: 5px;
   flex: 1;
   background: $white;

   &__header {
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

   &__nav {
     padding: 10px 10px;
     text-transform: uppercase;
     font-size: 13px;
     border-bottom: 1px solid $border;
   }

   &__item {
     display: inline-block;
     padding-right: 15px;
     font-size: 11px;
     font-weight: 500;
     line-height: 7px;
     text-transform: uppercase;
     cursor: pointer;
   }

   .scoringTab {
    color: $selected-green;
   }   

 }


</style>
