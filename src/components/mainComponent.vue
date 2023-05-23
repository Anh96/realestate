<template>
    <main>
        <section class="search search-container pd-10">
            <div class="pd-20">
                <div class="search__heading orange-text flex-center hithere">
                    <h1>Tìm ngay</h1>
                </div>
                <form class="search-box-tabs-container mt-20">
                    <div class="search-box-tabs">
                        <ul class="search-box-tabs__list">
                            <li class="search-box-tab__item pd-10 active orange-text">Nhà phố</li>
                            <li class="search-box-tab__item pd-10 orange-text"> Đất nền</li>
                            <li class="search-box-tab__item pd-10 orange-text"> Chung cư</li>
                        </ul>
                    </div>
                    <div class="search-box__input-container bg-brown pd-10">
                        <div class="input-container-box bg-white pd-10">
                            <button type="submit" class=" button search-button pd-10 flex">
                                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="white" class="bi bi-search flex" viewBox="0 0 16 16">
                                    <path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"/>
                                </svg>
                                <span class="white-text flex" style="font-size: 20px; font-weight: 300;">Tìm kiếm</span>
                            </button>
                            <input type="search" name="" class="pd-10" placeholder="Nhập tên quận/dự án cần tìm">
                        </div>
                        <ul class="home-filter home-filter--list">
                            <li class="home-filter__item home-filter__item-location pd-10">
                                <div class="select-text" v-on:click="toggleParentLocation()">
                                    <div class="white-text flex">Chọn nơi bán</div>
                                    <div class="flex">
                                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="white" class="bi bi-caret-down" viewBox="0 0 16 16">
                                            <path d="M3.204 5h9.592L8 10.481 3.204 5zm-.753.659 4.796 5.48a1 1 0 0 0 1.506 0l4.796-5.48c.566-.647.106-1.659-.753-1.659H3.204a1 1 0 0 0-.753 1.659z"/>
                                        </svg>
                                    </div>
                                </div>
                                <div class="listing-filter-popup listing-filter-popup-location-inner" v-show="parentLocationState">
                                    <div class="listing-filter-popup-header gray-text pd-10">Chọn khu vực</div>
                                    <div class="listing-filter-popup-body gray-text pd-10">
                                        <div class="filter-popup-body-select-item pd-10">
                                            <div class="filter-popup-body-select-item-text full-w" :city-name="currentCityName"
                                            v-on:click="detailLocationState=!detailLocationState; cityState = !cityState;toggleParentLocation()">
                                            {{ currentCityName }}</div>
                                            <div class="filter-popup-body-select-item-icon city-icon-group flex-center">
                                                <i class="bi bi-chevron-right gray-text flex-center"
                                                    v-on:click="detailLocationState=!detailLocationState; cityState = !cityState;toggleParentLocation()"
                                                    v-show="!rightArrowIconState">
                                                </i>
                                                <i class="bi bi-x gray-text flex-center" 
                                                    v-show="closeIconState"
                                                    @click="toggleRightArrowIcon(); 
                                                    toggleCloseIcon(); 
                                                    currentCityName = originCityName">
                                                </i>
                                            </div>
                                        </div>
                                        <div class="filter-popup-body-select-item pd-10">
                                            <div class="filter-popup-body-select-item-text full-w">Quận/Huyện</div>
                                            <i class="bi bi-chevron-right gray-text flex-center" v-show="!rightArrowIconState"></i>
                                            <i class="bi bi-x gray-text flex-center" v-show="closeIconState"></i>
                                        </div>
                                        <div class="filter-popup-body-select-item pd-10">
                                            <div class="filter-popup-body-select-item-text">Xã/Phường</div>
                                            <i class="bi bi-chevron-right gray-text flex-center" v-show="!rightArrowIconState"></i>
                                            <i class="bi bi-x gray-text flex-center" v-show="closeIconState"></i>
                                        </div>
                                        <div class="filter-popup-body-select-item pd-10">
                                            <div class="filter-popup-body-select-item-text">Đường</div>
                                            <i class="bi bi-chevron-right gray-text flex-center" v-show="!rightArrowIconState"></i>
                                            <i class="bi bi-x gray-text flex-center" v-show="closeIconState"></i>
                                        </div>
                                    </div>
                                    <div class="listing-filter-popup-footer pd-10">
                                        <button type="reset" class="pd-10 reset-button gray-text">
                                            <i class="bi bi-arrow-repeat"></i>
                                            <span class="">Đặt lại</span>
                                        </button>
                                        <button type="submit" class="pd-10 apply-button white-text">Áp dụng</button>
                                    </div>
                                </div>
                                <!-- DETAIL LOCATION -->
                                <div class="listing-filter-popup-location" v-show="detailLocationState">
                                    <div class="listing-filter-popup-location-body gray-text pd-10">
                                        <div class="listing-filter-city-location" v-show="cityState">
                                            <div class="filter-popup-body-select-item pd-10"
                                                v-for = "(city, index) in data.cities" :key= "city.cityCode"
                                                v-on:click="toggleDetailLocation();toggleCity(index); toggleParentLocation()">
                                                <div class="filter-popup-body-select-item-text" ref="cityname">{{ city.cityName }}</div>
                                                <i class="bi bi-chevron-right gray-text flex-center"></i>
                                            </div>
                                        </div>
                                        <div class="listing-filter-district-location" v-for="(info, infoIndex) in data.cities" :key="infoIndex">
                                            <div class="filter-popup-body-select-item pd-10" v-for="(value,index) in info.cityInfo" :key="index" v-show = "distState">
                                                <div class="filter-popup-body-select-item-text">{{ value.nameDist}}</div>
                                                <i class="bi bi-chevron-right gray-text flex-center"></i>
                                            </div>
                                        </div>
                                        <div class="listing-filter-ward-location">
                                            <div class="filter-popup-body-select-item pd-10">
                                                <div class="filter-popup-body-select-item-text">Binh Hung Hoa</div>
                                                <i class="bi bi-chevron-right gray-text flex-center"></i>
                                            </div>
                                        </div>
                                        <div class="listing-filter-street-location">
                                            <div class="filter-popup-body-select-item-text">DS 14</div>
                                        </div>
                                    </div>
                                    <!-- <div class="listing-filter-popup-footer pd-10">
                                        <button type="reset" class="pd-10 reset-button">
                                            <i class="bi bi-arrow-repeat"></i>
                                            <span class="gray-text">Đặt lại</span>
                                        </button>
                                        <button type="submit" class="pd-10 apply-button white-text">Áp dụng</button>
                                    </div> -->
                                </div>
                            </li>
                            <li class="home-filter__item home-filter__item-progress-general home-filter__item-cost pd-10">
                                <div class="select-text">
                                    <div class="white-text flex">Mức giá </div>
                                    <div class="flex">
                                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="white" class="bi bi-caret-down" viewBox="0 0 16 16">
                                            <path d="M3.204 5h9.592L8 10.481 3.204 5zm-.753.659 4.796 5.48a1 1 0 0 0 1.506 0l4.796-5.48c.566-.647.106-1.659-.753-1.659H3.204a1 1 0 0 0-.753 1.659z"/>
                                        </svg>
                                    </div>
                                </div>
                                <div class="listing-filter-popup listing-filter-popup-cost">
                                    <div class="listing-filter-popup-header dark-text pd-10 flex">
                                        <input type="number" class="font-20 dark-text" name="min-cost" min="0" value="0">
                                        <i class="bi bi-arrow-right flex pd-10"></i>
                                        <input type="number" class="font-20 dark-text" name="max-cost" max="8000" value="8000">
                                    </div>
                                    <div class="listing-filter-popup-body dark-text pd-10">
                                        <div class="filter-popup-body-progressbar pd-10 flex">
                                            <div class="circle start-circle-progressbar"></div>
                                            <div class="progress progress-fill"></div>
                                            <div class="circle end-circle-progressbar"></div>
                                        </div>
                                        <div class="filter-popup-body-cost-item-container">
                                            <div class="filter-popup-body-cost-item pd-10" v-for="cost in data.costs" :key="cost">
                                                <div class="filter-popup-body-cost-item-text">{{ cost }}</div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </li>
                            <li class="home-filter__item home-filter__item-progress-general home-filter__item-area pd-10">
                                <div class="select-text">
                                    <div class="white-text flex">Diện tích</div>
                                    <div class="flex">
                                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="white" class="bi bi-caret-down" viewBox="0 0 16 16">
                                            <path d="M3.204 5h9.592L8 10.481 3.204 5zm-.753.659 4.796 5.48a1 1 0 0 0 1.506 0l4.796-5.48c.566-.647.106-1.659-.753-1.659H3.204a1 1 0 0 0-.753 1.659z"/>
                                        </svg>
                                    </div>
                                </div>
                                <div class="listing-filter-popup listing-filter-popup-area">
                                    <div class="listing-filter-popup-header dark-text pd-10 flex">
                                        <input type="number" class="font-20 dark-text"  placeholder="Từ">
                                        <i class="bi bi-arrow-right flex pd-10"></i>
                                        <input type="number" class="font-20 dark-text"  placeholder="Đến">
                                    </div>
                                    <div class="listing-filter-popup-body dark-text pd-10">
                                        <div class="filter-popup-body-progressbar pd-10 flex">
                                            <div class="circle start-circle-progressbar"></div>
                                            <div class="progress progress-fill"></div>
                                            <div class="circle end-circle-progressbar"></div>
                                        </div>
                                        <div class="filter-popup-body-cost-item-container">
                                            <div class="filter-popup-body-cost-item pd-10" v-for="area in data.areas" :key="area">
                                                <div class="filter-popup-body-cost-item-text">{{ area }}</div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </li>
                        </ul>
                    </div>
                </form>
            </div>
        </section>
        <section class="main-content">
            <mainContentComponent></mainContentComponent>
            <sidebarComponent></sidebarComponent>
        </section>
    </main>
</template>

<script>
import data from "../csdl/data.json";
import sidebarComponent from './sidebarComponent.vue';
import mainContentComponent from "./mainContentComponent.vue";
export default {
    name : "main-component",
    data(){
        return {
            data: data,
            citySelected: null,
            distSelected: 0,
            wardSelected: 0,
            streetSelected: 0,
            rightArrIconSelectd: 0,
            closeIconSelected: 0,
            parentLocationState: false,
            detailLocationState: false,
            cityState: false,
            distState: false,
            wardState: false,
            streetState: false,
            rightArrowIconState: false,
            closeIconState: false,
            originCityName: "Tỉnh/Thành phố",
            currentCityName: "Tỉnh/Thành phố"
        }
    },
    components:{
        sidebarComponent,
        mainContentComponent
    },
    methods:{
        toggleParentLocation: function(){
            return this.parentLocationState = !this.parentLocationState;
        },
        toggleDetailLocation: function(){
            return this.detailLocationState = !this.detailLocationState;
        },
        toggleCity: function(currindex){
            this.cityState = !this.cityState;
            this.handleCity(currindex);
            this.handleIcons()
        },
        toggleDist: function(){
            return this.distState = !this.distState;
        },
        toggleWard: function(){
            return this.wardState = !this.wardState;
        },
        toggleStreet: function(){
            return this.streetState = !this.streetState;
        },
        toggleRightArrowIcon: function(currIndex){
            this.rightArrowIconState = ! this.rightArrowIconState;
        },
        toggleCloseIcon: function(currIndex){
            this.closeIconState = ! this.$el[currIndex].closeIconState;
        },
        handleCity: function(currIndex){
            this.currentCityName = this.$refs.cityname[currIndex].innerHTML;
        },
        handleIcons: function(){
            
        }
    },
    computed:{
    },
    props:{
        // currentCityName: String
        
    },
    emits: {
    }
}
</script>

<style >
    @import url("../css/style.css");
</style>
