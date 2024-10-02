<template>
    <div>
        Ngày sinh: {{ dateOfBirth }} <br>
        <input v-model="dateOfBirth" type="date">
    </div>
</template>

<script setup>
import { ref } from 'vue';
    const dateOfBirth = ref("");
</script>

<style>

</style>