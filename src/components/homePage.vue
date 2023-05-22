<template>
    <div id="home">
        <!-- header component -->
        <header-component></header-component>
        <!-- main component -->
        <main-component></main-component>
        <!-- footer component -->
        <footer-component></footer-component>
    </div>
</template>
<script>
import headerComponent from "./headerComponent.vue";
import mainComponent from "./mainComponent.vue";
import footerComponent from "./footerComponent.vue";
export default {
    name: "home-page",
    data(){
        return {
            msg: 'Welcome to Your Home Page'
      }
    },
    components:{
        headerComponent,
        mainComponent,
        footerComponent
    }
}
</script>

<style>
    @import url("../css/style.css");
</style>
