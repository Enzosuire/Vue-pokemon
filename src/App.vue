<script setup>
import Header from "./components/Header.vue"
import Footer from "./components/Footer.vue";
import Recherche from "./components/Recherche.vue";
import { onBeforeMount, ref } from "vue";
// const Recherche = document.querySelector("select");

const allPokemon = ref([]);
onBeforeMount(() => {

  fetch(`https://pokebuildapi.fr/api/v1/pokemon/`)
    .then((response) => response.json())
        
    .then((data) => {

      allPokemon.value = data;
      console.log(allPokemon.value);


        allPokemon.value = data.sort((a, b) => {
        const nameA = a.name.toLowerCase();
        const nameB = b.name.toLowerCase();
        if (nameA < nameB) {
          return -1;
        }
        if (nameA > nameB) {
          return 1;
        }
        return 0;
      });
    });
})
    

 
</script>

<template>
  <Header />


  <main id="main">

    <Recherche :pokemonList = "allPokemon" />

  </main>


  <Footer />
  
</template>



<style>
@import "./assets/styles.css";

@import url(https://fonts.googleapis.com/css2?family=Crimson+Text&family=Press+Start+2P&display=swap);
</style>

