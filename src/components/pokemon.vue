<template >
  <div >
        <h3  v-on:click="getPokemonDetails" >{{this.pokemon.name }}</h3 >
        <PokemonDetails v-if="pokemonDetails" :pokemonDetails="pokemonDetails" />
  </div>
</template>
<script>
import axios from 'axios';
import PokemonDetails from './PokemonDetails'

export default {
  name: 'Pokemon', 
   props: ['pokemon'], 
  components: { PokemonDetails },
   methods: {
    getPokemonDetails: function (event) {
      if(this.pokemonDetails === null){ // pas de données, on en récupère (ouvre le détail)
        axios
          .get(this.pokemon.url)
          .then(response => {
            console.log(response)
            this.pokemonDetails = response.data
          })
      }else{
        this.pokemonDetails = null; // pour "fermer" le detail
      }
     
    }
  },
  data () {
    return {
      pokemonDetails: null
    }
  },
};
</script>