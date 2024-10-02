<template>
    <div>
        <h1>Oneway data biding</h1>
        <h3>userName: {{ userName }}</h3>
        <input type="text" :value="userName">
        <button @click="handleClick">Change name</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';
    const userName = ref("Nguyễn Văn A");
    const handleClick = ()=>{
        userName.value = "Nguyễn Văn B";
    }
</script>

<style>

</style>