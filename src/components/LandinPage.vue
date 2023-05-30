<script setup lang="ts">
import router from '@/router';

    function moveUser() {
        router.push("/gameplay")
    }
</script>

<template>
    <h1>Welcome to the heads up game</h1>
    <button @click="moveUser()">Start Game</button>
</template>

<style scoped>

</style>