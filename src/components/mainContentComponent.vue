<template>
    <div class="card-container w-75 mr-10" style="">
        <div class="card-title">
            <h1 class="flex-center">Tìm nhà Tân Phú</h1>
        </div>
        <div class="card-list-wrapp">
            <ul class="card-list">
                <li class="card-item pd-10 mb-10 mr-10" v-for="(home, index) in data.homies" :key="index">
                    <a href="" class="card-item-link">
                        <div class="card-item-img bg-white">
                            <img src="../assets/bg-full-0.jpg" alt="">
                        </div>
                        <div class="card-item-information bg-white font-15 mt-10">
                            <div class="card-item-information-title dark-text mr-10 ">
                                <div class = "card-item-information-title--twhd" >{{ home.title}}</div>
                            </div>
                            <div class="card-item-information-config orange-text mt-10 ml-10">
                                <div class="card-item-information-config-price flex-center mr-10">
                                    <i class="bi bi-cash-stack flex-center mr-10"></i>
                                    <div class="flex-center">
                                        <div class="flex-center">{{ home.price / 1000000000}}</div>
                                        <div class="flex-center">tỷ</div>     
                                    </div>
                                </div>
                                <div class="card-item-information-congif-area flex-center">
                                    <i class="bi bi-rulers flex-center mr-10"></i>
                                    <div class="flex-center">
                                        <div class="flex-center">{{ home.area }}</div>
                                        <div class="flex-center">m2</div>
                                    </div>
                                </div>
                                <div class="card-item-information-congif-area flex-center ml-10">
                                    <i class="bi bi-badge-wc-fill flex-center"></i>
                                    <div class="flex-center">
                                        <div class="flex-center ml-10">{{ home.wc }}</div>
                                    </div>
                                </div>
                            </div>
                            <div class="card-item-information-location dark-text mt-10 ml-10">
                                <i class="bi bi-geo-alt-fill flex-center mr-10"></i>
                                <div class=" text-capitalize flex-center">{{ home.district }}</div>
                            </div>
                            <div class="card-item-information-contact dark-text mt-10 ml-10">
                                <div class="card-item-information-published-at flex-center mr-10">Đăng hôm nay</div>
                                <i class="bi bi-telephone-fill flex-center mr-10"></i>
                            </div>
                        </div>
                    </a>
                </li>
                <div></div>
            </ul>
            <div class="card-button mt-20 flex-center">
                <button class="show-more text-upercase pd-10" v-on:click="handleShowCardItem()"><strong>Xem thêm</strong></button>
            </div>
        </div>
    </div>
</template>

<script>
import data from "../csdl/data.json"
export default {
    name: "mainContentComponent",
    data(){
        return {
            data: data
        }
    }
}
</script>

<style>
    @import "../css/style.css";
</style>