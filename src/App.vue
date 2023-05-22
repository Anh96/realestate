<template>
    <div id="app">
      <home-page></home-page>
    </div>
  </template>
  
  <script>
  import homePage from "./components/homePage.vue";
  export default {
    name: 'app',
    data () {
      return {
        msg: 'Welcome to Your Vue.js App'
      }
    },
    components: {
      homePage
    },
    computed: {
  
    }
  }
  </script>
  
  <style>
    @import url("./css/style.css");
  </style>
  