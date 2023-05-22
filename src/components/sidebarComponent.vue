<template>
    <section class="sidebar w-25 mt-20">
        <div class='sidebar-container pd-20'>
            <h1 class="sidebar-heading">Để lại thông tin, chúng tôi sẽ hỗ trợ ngay</h1>
            <form action="sidebar-form">
                <div class="phone-number-container mb-10 mt-20 flex">
                    <label for="" class="mr-10">Số điện thoại</label>
                    <input type="text" class="pd-10" placeholder="Nhập số điện thoại...">
                </div>
                <div class="customer-question">
                    <textarea name="" id="" row placeholder="Nhập nội dung bạn cần chúng tôi hỗ trợ"></textarea>
                </div>
                <div class="sidebar-button flex-center">
                    <button class="pd-10 text-upercase"><strong>Gửi</strong></button>
                </div>
            </form>
        </div>
    </section>
</template>

<script>
export default {
    name: "sidebarComponent",
    data(){
        return{
            data: [],
        }
    }
}
</script>

<style>
    @import url("../css/style.css");
</style>