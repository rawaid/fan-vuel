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
@import "../styles/colors.scss";

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
