<template>
    <div>
        <div>Giới tính: {{ gender }}</div>
        <div>
            Nam <input v-model="gender" name="gender" value="Nam" type="radio">
            Nữ <input v-model="gender" name="gender" value="Nữ" type="radio">
            Khác <input v-model="gender" name="gender" value="Khác" type="radio">
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';
    const gender = ref("Nam");
</script>

<style>

</style>