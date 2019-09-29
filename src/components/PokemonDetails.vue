<template>
  <div>
        <h2>{{this.pokemonDetails.id}}</h2>
  </div>
</template>
<script>
export default {
  name: 'PokemonDetails', 
   props: ['pokemonDetails']
};
</script>