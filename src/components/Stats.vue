<template>
  <div class="stats-container">
    <div class="stats-container__header">
      Stats
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'


export default {
  name: 'Stats',
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

 .stats-container {

   margin: 5px;
   background: $white;
   min-height: 427px;
   height: 100%;
   flex: 1;

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

}

</style>
