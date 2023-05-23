<template>
    <main>
        <section class="search-home">
            <search-home-component></search-home-component>
        </section>
        <section class="main-content">
            <mainContentComponent></mainContentComponent>
            <sidebarComponent></sidebarComponent>
        </section>
    </main>
</template>

<script>
import searchHomeComponentVue from "./searchHomeComponent.vue"
import sidebarComponent from './sidebarComponent.vue';
import mainContentComponent from "./mainContentComponent.vue";
import SearchHomeComponent from './searchHomeComponent.vue';
export default {
    name : "main-component",
    data(){
        return {
        }
    },
    components:{
        sidebarComponent,
        mainContentComponent,
        SearchHomeComponent
    }
}
</script>

<style >
    @import url("../css/style.css");
</style>
