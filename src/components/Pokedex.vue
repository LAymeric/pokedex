<template>
  <div class="pokedex">
    <h1>{{ msg }}</h1>
     <Pokemon v-for="poke in info.data.results" v-bind:poke="poke" 
    v-bind:key="poke.id" :pokemon="poke"/>
  </div>

</template>

<script>
import axios from 'axios';
import Pokemon from './Pokemon';

export default {
  name: 'Pokedex', 
  components: { Pokemon },
  data () {
    return {
      msg: 'Pokedex',
      info: {
        data: {
          results: []
        }
      }
    }
  },
  mounted () {
    axios
      .get('https://pokeapi.co/api/v2/pokemon/?limit=151')
      .then(response => (this.info = response))
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

