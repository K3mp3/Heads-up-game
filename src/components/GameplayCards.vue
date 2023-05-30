<script setup lang="ts">
import { ref } from "vue";
import type { IGameCard } from "../Models/IGameCard"


const dogBreed = ref<IGameCard[]>([
    {name: "Siberian husky", shown: true, picture: "/images/siberian-husky.jpg"},
    {name: "Mops", shown: false, picture: "images/pug.jpg"},
    {name: "Cocker spaniel", shown: false, picture: "images/cocker-spaniel.jpg"},
    {name: "Golden retriever", shown: false, picture: "images/golden-retriever.jpg"},
    {name: "Shiba", shown: false, picture: "images/shiba.jpg"},
    {name: "Chihuahua", shown: false, picture: "images/chihuahua.jpg"},
    {name: "Australian Shepherd", shown: false, picture: "images/australian-shepherd.jpg"},
    {name: "Pudel", shown: false, picture: "images/poodle.jpg"},
    {name: "Rottweiler", shown: false, picture: "images/rottweiler.jpg"},
    {name: "Labrador", shown: false, picture: "images/labrador.jpg"},
]);

let currentIndex = 0;
let totalPoints = 0;

const emits = defineEmits<{ (e: "points", totalPoints: number): void }>();

function nextBreed(dog: IGameCard, passed: boolean) {
    currentIndex ++;

    dog.shown = false;

    let currentDogBreed = dogBreed.value[currentIndex].name;
    let currentDogBreedShown = dogBreed.value[currentIndex].shown = true;
    console.log("currentDogBreed", currentDogBreed, "currentDogBreedShown", currentDogBreedShown)

    if (passed) {
        console.log("passed", passed)
        totalPoints ++;
        console.log("totalPoints", totalPoints)

        emits ('points', totalPoints);
    } else {
        console.log("did not passed", passed)
    }
}

const hideDog = "hideDog";
</script>

<template>
    <div v-for="dog in dogBreed.filter(dog => dog.shown)">
        <h1>{{ dog.name }}</h1>
        <p>{{ dog }}</p>
        <img :src="dog.picture" alt="dog" />
        <button @click='() => nextBreed(dog, true)'>✔</button>
        <button @click='() => nextBreed(dog, false)'>✘</button>
    </div>

    <img src="/src/assets/siberian-husky.jpg" alt="" />
</template>

<style scoped>
    .hideDog {
        visibility: hidden;
        display: none;
    }
</style>