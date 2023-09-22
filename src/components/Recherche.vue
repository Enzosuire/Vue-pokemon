<script setup>
import { ref } from "vue";
import DetailsPokemon from "./DetailsPokemon.vue";

const props = defineProps({
  pokemonList: Array,
});
const isPokemon = ref(false);
const pokemonSelected = ref("");
const pokemonDatas = ref ({});
function chercherpokemon() {
  console.log("bouton cliqué");
  fetch(`https://pokebuildapi.fr/api/v1/pokemon/` + pokemonSelected.value)
    .then((response) => response.json())

    .then((pokemon) => {
      console.log("Pokemon recupéré", pokemon);
      pokemonDatas.value = pokemon;
      isPokemon.value = true;
    });
  }

</script>



<template>
  <!-- <form id="selectedPokemon" name="FormPokemon" action="post"> -->
  <h1>INFORMATIONS POKEMON</h1>

  <select name="" id="" v-model="pokemonSelected">
    <option v-for="pokemon in pokemonList" :value="pokemon.id">
      {{ pokemon.name }}
    </option>
  </select>
  <!-- Pokemon selectionné :{{ pokemonSelected }} -->
  <button @click="chercherpokemon" type="button">Chercher</button>
  <DetailsPokemon v-if="isPokemon === true" :pokemonDetails="pokemonDatas"/>

  

  <!-- <p>Pour connaitre ses caractéristiques  <button type="submit">Chercher via JS</button></p> -->

  <!-- </form>
<section class="resultat">
     <h2></h2>
     <img src="" alt="">
     <p></p>
     <p></p>

     <button  id="details" type="submit"> Details</button>  
     
</section>

<button id="retour" >retour</button> -->
</template>
