<script setup lang="ts">
    import GameplayCards from "./GameplayCards.vue"

    function showTotalPoints(points: number) {
        console.log("showTotalPoints", points);
    }
</script>

<template>
    <article>
        <GameplayCards @points="showTotalPoints"></GameplayCards>
    </article>
</template>

<style scoped>
    article {
        width: 800px;
        height: 500px;
        margin: auto;
        background-color: #65a3de;
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>