<template>
  <div>
    <span>{{this.pokemonDetails.id}}</span>
    <span v-for="type in pokemonDetails.types.length" v-bind:key="type" :type="type">{{type.name}}</span>
  </div>
</template>
<script>
export default {
  name: 'PokemonDetails',
  props: ['pokemonDetails'],
  data () {
    return {
      type: null
    }
  }
}
</script>
