/* eslint-disable */
<template>
   <div v-if="dataLoaded">
      <header class="global-header">
        <div class="global-header__container">
          <section class="logo-container">
              <a href="/"><img class="logo" src="../assets/logo.png" alt="FanDuel Logo"/></a>
          </section>

          <nav class="primary-nav">
              <ul class="primary-nav__list">
                <li v-for="item in nav" v-bind:class="{selected: item.title=='Live'}" class="primary-nav__item"><a class="primary-nav__anchor" v-bind:href="item.href">{{item.title}}<i v-if="item.title=='Live'" class="fas fa-angle-down global-header__arrow"></i></a></li>
            </ul>
          </nav>

          <nav class="sidebar-nav" v-bind:class="{active:isActive}">
              <ul class="sidebar-nav__list">
                <li class="sidebar-nav__item"><a class="sidebar-nav__anchor" href="/">Lobby</a></li>
                <li class="sidebar-nav__item"><a class="sidebar-nav__anchor" href="/">Upcoming</a></li>
                <li class="sidebar-nav__item selected"><a class="sidebar-nav__anchor" href="/">Live <i class="fas fa-angle-down"></i>
                </a></li>
                <li class="sidebar-nav__item"><a class="sidebar-nav__anchor" href="/">History</a></li>
                <li class="sidebar-nav__item"><a class="sidebar-nav__anchor" href="/">Help</a></li>
                <li class="sidebar-nav__item"><a class="sidebar-nav__anchor" href="/">nbonnadio</a></li>
                <li class="sidebar-nav__item"><a class="sidebar-nav__anchor" href="/">Add Funds</a></li>

            </ul>
            <button class="sidebarBtn" v-on:click="expand">
              <span></span>
            </button>
          </nav>

          <nav class="secondary-nav">
              <ul class="secondary-nav__list">
                <li class="secondary-nav__item hide-for-medium"><a class="secondary-nav__anchor" href="/">Help <i class="fas fa-angle-down"></i></a></li>
                <li class="secondary-nav__item"><a class="secondary-nav__anchor" href="/"><img class="secondary-nav__icon" src="../assets/user.gif"/>nbonnadio <i class="fas fa-angle-down"></i></a></li>
                <li class="secondary-nav__item"><a class="secondary-nav__anchor" href="/"><div class="secondary-nav__balance"><div>$1,000,000.00</div><div>BALANCE</div></div><div class="secondary-nav__button">Add funds</div></a></li>
              </ul>
          </nav>

        </div>
      </header>
    </div>
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
      nav: [],
      dataLoaded: false,
      isActive: false
    }
  },
  methods: {
    expand: function(e){
      this.isActive = !this.isActive;
    }
  },
  mounted() {
    Vue.axios.get("https://my-json-server.typicode.com/fanduel/moneyball-fe-challenge-data/nav_elements").then((response) => {
      this.dataLoaded = true;
      this.nav = response.data;
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import "../styles/colors.scss";

.global-header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  height: 66px;
  background: $fanduel-navy;
  color: $white;
  -webkit-font-smoothing: antialiased;
  font-size: 0.875rem;

  &__container {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    max-width: 100%;
    margin: 0 auto;
  }

  &__arrow {
    margin-left: 5px;
  }
}


.logo-container {
  padding-left: 0;
  padding-top: 10px;
  display: inline-block;
  position: relative;
}

.logo {
  height: 38px;
  width: 140px;
  padding-top: 5px;
  padding-left: 10px;
  display: flex;
  display: -webkit-box;
  display: -ms-flexbox;
 }

 .primary-nav,
 .secondary-nav {
  -webkit-box-flex: 0;
  -ms-flex: none;
  flex: none;

  &__list {
   display: flex;
   flex-wrap: wrap;
   list-style-type: none;
   margin: 0;
  }

  &__item {
    display: inline-block;
    list-style-type: none;
  }

  &__anchor {
    text-align: center;
    padding-right: 25px;
    padding-left: 25px;
    text-decoration: none;
    line-height: 66px;
    overflow: hidden;
    position: relative;

    &:link,
    &:visited,
    &:active {
      color: $white;
    }
  }
 }

  .secondary-nav {
   text-align: right;
   margin-left: auto;
   &__balance,
   &__balance div {
     display: inline;
     height: 66px;
   }

   &__balance div:nth-child(2) {
     position: absolute;
     display: block;
     top: -10px;
     left: 63px;
     bottom: 15px;
     font-size: 11px;
   }

   &__button {
     display: inline;
     border-radius: 3px;
     position: relative;
     top: 5px;
     padding: 6px 10px 6px 10px;
     background: $selected-green;
     font-size: 12px;
     margin-top: 5px;
     margin-left: 10px;
   }

   &__icon {
     position: relative;
     top: 15px;
     right: 10px;
   }
 }
 @media (max-width: 641px) {
  .primary-nav,
  .secondary-nav {
    display: none;
  }

  .logo-container {
    padding-left: 30%;
  }


   .global-footer {
     display: none;
   }

   .active {
    left: 0 !important;
  }

   .sidebar-nav {
     position: fixed;
     top: 0;
     left: -250px;
     background: $fanduel-navy;
     width: 250px;
     height: 100%;
     transition: .3s;

     &__list {
       margin: 0;
       padding: 20px 0;
     }

     &__item {
       list-style: none;
     }

     &__anchor {
       padding: 10px 20px;
       color: $white;
       display: block;
       text-decoration: none;
       border-bottom: 1px solid $other-games;

       &:hover {
         background: $fanduel-highlight;
       }
     }
   }

   .sidebarBtn {
    position: absolute;
    top: 0;
    right: -50px;
    width: 50px;
    height: 66px;
    box-sizing: border-box;
    cursor: pointer;
    background: $fanduel-navy;
    border: none;
    outline: none;

    & span {
     display: block;
     width: 35px;
     height: 3px;
     background: $white;
     position: absolute;
     top: 30px;
     transition: .3s;
    }

    & span:before {
      content: '';
      position: absolute;
      top: -10px;
      left: 0;
      width: 100%;
      height: 3px;
      background: $white;
    }

    & span:after {
     content: '';
     position: absolute;
     top: 10px;
     left: 0;
     width: 100%;
     height: 3px;
     background: $white;
   }
  }
 }

  @media (min-width: 641px) {
   .content {
     padding-left: 5%;
     padding-right: 5%;
   }
   .sidebar-nav {
     display: none;
   }
 }

 @media (min-width: 624px) and (max-width: 800px){
  .secondary-nav {
    display: none;
  }
 }

</style>
