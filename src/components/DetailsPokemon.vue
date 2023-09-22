<script setup>
const props = defineProps({
    pokemonDetails: Object,
});
</script>

<template>
    
    <h2>Detail de {{ pokemonDetails.name }}</h2>
    <p>Élément : {{pokemonDetails.apiTypes.map((type)=> type.name).join(" / ") }}</p>
    <!-- <p>Évolution : {{ pokemonDetails.apiEvolutions.map((evolution)=> evolution.name).join(" / ")}}</p> -->
    <p v-if="pokemonDetails.apiEvolutions[0] !== undefined">Évolution : {{ pokemonDetails.apiEvolutions.map((evolution)=> evolution.name).join(" / ")}}</p>
    <p v-else>Evolution : Aucune</p>
    <img v-bind:src="pokemonDetails.image" alt="{{ pokemonDetails.name }}">
    <p>Les statistiques :</p>
    <p>Points de vie : {{pokemonDetails.stats.HP}}</p>
    <p>Attaque : {{pokemonDetails.stats.attack}}</p>
    <p>Défense : {{pokemonDetails.stats.defense}}</p>
    <p>Attaque spécial : {{pokemonDetails.stats.special_attack}}</p>
    <p>Défense spécial : {{pokemonDetails.stats.special_defense}}</p>
    <p>Vitesse : {{pokemonDetails.stats.speed}}</p>

   
</template>

