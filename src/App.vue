<template>
  <div id="app">
    <!--<img src="./assets/logo.png">-->
    <router-view/>
    <!-- <lift-nav></lift-nav> -->
  </div>
</template>

<script>
  import LiftNav from './components/lift-nav'
export default {
  name: 'App',
  components:{
    'lift-nav': LiftNav
  }
}
</script>

<style>
/*#app {*/
  /*font-family: 'Avenir', Helvetica, Arial, sans-serif;*/
  /*-webkit-font-smoothing: antialiased;*/
  /*-moz-osx-font-smoothing: grayscale;*/
  /*text-align: center;*/
  /*color: #2c3e50;*/
  /*margin-top: 60px;*/
/*}*/
</style>
