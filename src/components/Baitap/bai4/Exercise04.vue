<template>
    <div>
        Tiến độ hoàn thành: {{ completion }} %<br>
        <input v-model="completion" type="range">
    </div>
</template>

<script setup>
    import { ref } from 'vue';
    const completion = ref("");
</script>

<style>

</style>