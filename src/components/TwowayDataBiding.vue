<template>
    <form @submit.prevent="handleSubmit">
        <h2>userName: {{ userName }}</h2>
        <h2>Date of birth: {{ dateOfBirth }}</h2>
        <h2>Gender: {{ gender }}</h2>
        <h2>Sở thích: {{ hobbies }}</h2>
        <h3>Thêm mới người dùng</h3>
        <div>Họ và tên: <input v-model="userName" type="text" placeholder="Nhập tên"></div>
        <div>Ngày sinh: <input v-model="dateOfBirth" type="date"></div>
        <div>Giới tính: </div>
        <div>
            Nam <input name="gender" v-model="gender" type="radio" value="0"> Nữ <input name="gender" v-model="gender" type="radio" value="1"> khác 
            <input name="gender" v-model="gender" type="radio" value="2">
        </div>
        <div>
            Sở thích
        </div>
        <div>
            Chơi game <input value="playgame" v-model="hobbies" type="checkbox">
            code <input value="code" v-model="hobbies" type="checkbox">
            bơi lội <input value="swim" v-model="hobbies" type="checkbox">
        </div>
        <button>Thêm</button> 
    </form>
</template>

<script setup>
import { reactive, ref } from 'vue';
    const userName = ref("");
    const dateOfBirth = ref("");
    const gender = ref("0");
    const hobbies = ref([]);
    const handleSubmit = (e)=>{
        //Ngăn chặn sự kiện load lại trang
        // e.preventDefault();
        // console.log("submited");
    }
    const user = {
        userName: userName.value,
        dateOfBirth: dateOfBirth.value,
        gender: gender.value,
        hobbies: hobbies.value
    }
    const userInfo = reactive({
        userName: "",
        dateOfBirth:"",
        gender: "0",
        hobbies: [],
    })
</script>

<style>

</style>