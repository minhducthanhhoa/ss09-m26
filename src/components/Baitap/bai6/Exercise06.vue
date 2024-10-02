<template>
    <div>
        <div>Sở thích: {{ hobbies }}</div>
        <div>
            Đá bóng <input value="football" v-model="hobbies" type="checkbox">
            Bóng chuyền <input value="volleyball" v-model="hobbies" type="checkbox">
            Code <input value="code" v-model="hobbies" type="checkbox">
            Bơi lội <input value="swim" v-model="hobbies" type="checkbox">
        </div>
    </div>
</template>

<script setup>
    import { ref } from 'vue';
    const hobbies = ref([]);
</script>

<style>

</style>