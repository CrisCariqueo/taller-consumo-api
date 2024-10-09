<template>
    <!-- dejarle evento que llame funcion -->
    <button @click="populationData">Datos Población</button>
    <button @click="animeRecomendationData">Recomendaciones anime</button>
    <button @click="animeData">Random anime</button>
    <button @click="mangaData">Random manga</button>

    <p>
        {{ shownData }}
    </p>
</template>

<script setup>
import { ref } from 'vue';

const shownData = ref([]);

// funcion llamada para llamar endpoint
const populationData = async () => {
    const response = await fetch('https://countriesnow.space/api/v0.1/countries/population');
    const populationData = await response.json();
    shownData.value = populationData.data;
    console.log(populationData.data);
};
const animeRecomendationData = async () => {
    const response = await fetch('https://api.jikan.moe/v4/recommendations/anime');
    const animeRecomendation = await response.json();
    shownData.value = animeRecomendation.data;
    console.log(animeRecomendation.data);
};
const animeData = async () => {
    const response = await fetch('https://api.jikan.moe/v4/random/anime');
    const animeData = await response.json();
    shownData.value = animeData.data;
    console.log(animeData.data);
};
const mangaData = async () => {
    const response = await fetch('https://api.jikan.moe/v4/random/manga');
    const mangaData = await response.json();
    shownData.value = mangaData.data;
    console.log(mangaData.data);
};
</script>

<style>

</style>