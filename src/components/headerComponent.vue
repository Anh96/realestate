<template>
    <header>
        <div class="top-message">
            <div class="top-mesage-wrapper">
                <ul class="top-message-list">
                    <li class="top-message-item-list">Mua nhà giá tốt - "chốt" nhà giá hời</li>
                    <li class="top-message-item-list">Gọi ngay đi - 078x.79x.xxx</li>
                    <li class="top-message-item-list">Mua nhà giá tốt - "chốt" nhà giá hời</li>
                    <li class="top-message-item-list">Gọi ngay đi - 078x.79x.xxx</li>
                    <li class="top-message-item-list">Mua nhà giá tốt - "chốt" nhà giá hời</li>
                    <li class="top-message-item-list">Gọi ngay đi - 078x.79x.xxx</li>
                </ul>
            </div>
        </div>
        <nav>
            <div class="nav-header container">
                <div class="logo">
                    <img class="logo__img" src="../assets/OJYTSM1-ai.png" style="object-fit: fill;">
                </div>
                <ul class="nav-list">
                    <li class="nav-item" v-for="(item, index) in listItems" :key="index">
                        <a href="#" class="nav-item-link orange-text" 
                        @click="changingTabActive(index)"
                        v-bind:class="{active: (index === navSelected)}">{{ item}}</a>
                    </li>
                </ul>
            </div>
        </nav>
    </header>
</template>

<script>
export default {
    name: "header-component",
    data() {
        return {
            listItems: ["trang chủ", "danh mục bất động sản", "giới thiệu", "liên hệ"],
            navSelected: 0
        }
    },
    methods:{
        changingTabActive: function(currentIndex){
            this.navSelected = currentIndex;
        }
    }    
}
</script>

<style>
    @import url("../css/style.css");
</style>