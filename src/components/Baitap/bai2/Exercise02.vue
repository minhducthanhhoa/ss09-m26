<template>
    <div>
        Màu sắc: <input v-model="color" type="color">
        <p>Mã màu: {{ color }}</p>
    </div>
</template>

<script setup>
import { ref } from 'vue';
    const color = ref("");
</script>

<style>

</style>