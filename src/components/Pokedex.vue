<template>
  <div class="container-pokedex">
    <div class="pokedex">
      <h1>{{ title }}</h1>
    </div>
    <div id="circle">
      <div id="circle-2" :style="{backgroundColor: backgroundcolor}"></div>
    </div>
    <div class="container-info">
      <form class="search">
        <div>
            <div>
                <input type="text" id="searchPokemon" placeholder="Enter a Pokemon or his ID"/>
                <input type="submit" value="Search" v-on:click="getPokemon" class="btn btn-outline-danger"/>
            </div>
            <div class="error">
                <span v-if="msgError">{{msgError}}</span>
            </div>
        </div>
      </form>
      <Pokemon  v-if="pokemonDetails" :pokemon="pokemonDetails"/>
    </div>
  </div> 
</template>
<script>
import axios from 'axios'
import Pokemon from './Pokemon'

export default {
  name: 'Pokedex',
  components: { Pokemon },
  data () {
    return {
      title: 'My Pokedex',
      backgroundcolor: '#FFFFFF',
      pokemonDetails:null,
      searchPokemon: null,
      msgError: null,
    }
  },
  methods: {
    getPokemon: function (event) {
      console.log(searchPokemon.value)
      if (searchPokemon.value && searchPokemon.value !== "") {
        this.msgError = null
        axios.get("https://pokeapi.co/api/v2/pokemon/" + searchPokemon.value.toLowerCase()).then(response => {
        console.log(response)
        this.isCatched(response)
        this.pokemonDetails = response.data
      }).catch((e)=>{
          console.log(e)       
          this.backgroundcolor = '#E80000',
          this.msgError = 'Your pokemon is undefined'
          this.pokemonDetails = null
        
        }) 
      } 
    },
    isCatched: function(response) {
        if (response.status === 200) {
          this.backgroundcolor = '#89D800'
        } 
    }
  }
}
</script>
