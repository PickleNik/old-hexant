<template>
  <v-app dark class="dark2">

    <v-navigation-drawer disable-resize-watcher floating fixed app v-model="drawer" class="hidden-md-and-up pt-5 dark3" style="width: 50%;">
      <v-list-tile v-ripple to="about" class="mt-4">
        <v-icon left class="grey--text">attach_file</v-icon>
        <v-list-tile-title>About</v-list-tile-title>
      </v-list-tile>
      <v-list-tile v-ripple to="home">
        <v-icon left class="grey--text">home</v-icon>
        <v-list-tile-title>Home</v-list-tile-title>
      </v-list-tile>
      <v-list-tile v-ripple to="cart">
        <v-icon left class="grey--text">shopping_cart</v-icon>
        <v-list-tile-title>Cart</v-list-tile-title>
      </v-list-tile>
      <v-list-tile v-ripple to="cart">
        <v-icon left class="grey--text">exit_to_app</v-icon>
        <v-list-tile-title>Login</v-list-tile-title>
      </v-list-tile>
    </v-navigation-drawer>

    <v-toolbar fixed app style="z-index: 99;" class="hidden-md-and-up elevation-0 dark3">
      <v-btn icon color="grey--text" @click="drawer = !drawer"><v-icon>{{ drawer ? 'close' : 'menu' }}</v-icon></v-btn>
      <Hex class="zoom delay-2" style=" top: -5px; position: fixed; left: 50%; transform:translateX(-50%);"/>
      <img style="z-index:1;" class="mx-auto mt-3" width="60" height="69.265"  src="@/assets/HexantLogo.png" alt="alt">
      <v-btn icon disabled></v-btn>
    </v-toolbar>

    <div class="triangle-left hidden-md-and-up"></div>
    <div class="triangle-right hidden-md-and-up"></div>

    <v-flex md3 lg2 class="hidden-sm-and-down" style="position: fixed; left: 1em; top: 1em;">
      <v-layout column>
        <v-layout row>
          <img @click="$router.push('/home')" class="zoom delay-1 ml-1 logo" width="70" height="80.826" src="@/assets/HexantLogo.png" alt="alt" style="curseor: pointer;">
          <h1 @click="$router.push('/home')" class="ml-4" style="max-height: 1.5em; margin-top: 0.7em;"> Hexant</h1>
        </v-layout>
        <Hex @click.native="$router.push('/about')" icon="attach_file" color="purple lighten-1" class="zoom delay-2 mt-3 ml-5"/>
        <Hex @click.native="$router.push('/cart')" icon="shopping_cart" color="indigo lighten-1" class="zoom delay-3 mt-3 ml-1"/>
      </v-layout>
    </v-flex>

    <v-content class="hidden-md-and-up">
      <router-view/>
    </v-content>

    <v-flex class="hidden-sm-and-down" style="margin: 0 220px;">
      <router-view/>
    </v-flex>

    <v-flex md3 lg2 class="hidden-sm-and-down" style="position: fixed; left: 1em; bottom: 0.6em;">

    </v-flex>

  </v-app>
</template>

<script>
import Hex from '@/components/Hex.vue'

export default {
  name: 'App',
  components: {
    Hex
  },
  data () {
    return {
      drawer: false
    }
  }
}
</script>

<style media="screen">
@import url('https://fonts.googleapis.com/css?family=Space+Mono');
  *{
    color: #aaa;
    font-family: 'Space Mono';
  }
  html, body{
    background: #111;
  }
  ::-webkit-scrollbar{
    width: 0;
  }
  .corner-cut{
    position: relative;
  }
  .corner-cut:before,
  .corner-cut:after {
   content: "";
   position: absolute;
   left: 0; right: 0;
   bottom: 100%;
   border-bottom: 15px solid #222;
   border-left: 25px solid transparent;
   border-right: 25px solid transparent;
  }

  .corner-cut:after {
    z-index:0;
   bottom: auto;
   top: 100%;
   border-bottom: none;
   border-top: 15px solid #222;
  }
  .triangle-right{
    position: fixed;
    right: 0;
    top: 56px;
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 0 25px 15px 0;
    border-color: transparent #222 transparent transparent;
  }
  .triangle-left{
    position: fixed;
    left: 0;
    top: 56px;
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 15px 25px 0 0;
    border-color: #222 transparent transparent transparent;
  }
  @keyframes zoom {
    from {
      opacity: 0;
      -webkit-transform: scale3d(.3, .3, .3);
              transform: scale3d(.3, .3, .3);
    }
    50% {
      opacity: 1;
    }
    100% {
      opacity: 1;
    }
  }
  .zoom{
    opacity: 0;
    animation: zoom 0.5s ease 1 forwards;
  }
  @keyframes zoom-rotate {
    from {
      opacity: 0;
      -webkit-transform: rotate(90deg) scale3d(.3, .3, .3);
              transform: rotate(90deg) scale3d(.3, .3, .3);
    }
    50% {
      opacity: 1;
    }
    100% {
      opacity: 1;
    }
  }
  .zoom-rotate {
    opacity: 0;
    animation: zoom-rotate 0.5s ease 1 forwards;
  }
  .one-by-one:nth-of-type(1){
    animation-delay: 0.1s;
  }
  .one-by-one:nth-of-type(2){
    animation-delay: 0.2s;
  }
  .one-by-one:nth-of-type(3){
    animation-delay: 0.3s;
  }
  .one-by-one:nth-of-type(4){
    animation-delay: 0.4s;
  }
  .one-by-one:nth-of-type(5){
    animation-delay: 0.5s;
  }
  .one-by-one:nth-of-type(6){
    animation-delay: 0.6s;
  }
  .one-by-one:nth-of-type(7){
    animation-delay: 0.7s;
  }
  .one-by-one:nth-of-type(8){
    animation-delay: 0.8s;
  }
  .one-by-one:nth-of-type(9){
    animation-delay: 0.9s;
  }

  .delay-1{
    animation-delay: 0.1s;
  }
  .delay-2{
    animation-delay: 0.2s;
  }
  .delay-3{
    animation-delay: 0.3s;
  }
  .delay-4{
    animation-delay: 0.4s;
  }
  .delay-5{
    animation-delay: 0.5s;
  }
  .delay-6{
    animation-delay: 0.6s;
  }
  .delay-7{
    animation-delay: 0.7s;
  }
  .delay-8{
    animation-delay: 0.8s;
  }
  .delay-9{
    animation-delay: 0.9s;
  }
  h1{
    transition-duration: 0.5s;
    transition-timing-function: ease;
    background-size: 0 0;
    cursor:pointer;
  }
  h1:hover{
    background: #E91E63;
    color: #222;
  }
  .logo{
    transition-duration: 0.5s;
    transition-timing-function: ease;
    transition-property: all;
    cursor: pointer;
  }
  .logo:hover{
    filter:grayscale(1);
  }
  .logo:active{
    transform: scale(1.1);
  }

</style>
