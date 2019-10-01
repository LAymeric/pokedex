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
        this.msgError = null
        axios.get("https://pokeapi.co/api/v2/pokemon/" + searchPokemon.value.toLowerCase()).then(response => {
        console.log(response)
        this.isCatched(response)
        this.pokemonDetails = response.data
      }).catch(
        console.log('test'),        
          this.backgroundcolor = '#E80000',
          this.msgError = 'Your pokemon is undefined'
        )
    },
    isCatched: function(response) {
        if (response.status === 200) {
          this.backgroundcolor = '#89D800'
        } 
    }
  }
}
</script>
<style>
@font-face {
   font-family: Pokemon;
   src: url(../assets/font/Pokemon.ttf);
}
  .pokedex{
    padding-top: 100px;
    background-color: brown;
    border-radius: 10px;
    border-bottom:10px solid black;
    color: rgb(235, 235, 37);
    text-shadow: blue 1px 1px, blue -1px 1px, blue -1px -1px, blue 1px -1px;
    height:280px;
    font-family: Pokemon;
  }
  .container-pokedex{
    border-radius: 20px;
    border: 5px solid black;
    width: 800px;
    margin: auto;
  }
  #circle{
    width:150px;
    height:150px;
    border-radius:50%;
    position:relative;
    top:-80px;
    background-color:white;
    border:10px solid black;
    margin: auto;
    }
  #circle-2{
    width:75px;
    height:75px;
    border-radius:50%;
    position:relative;
    top: 28px;
    border:5px solid black;
    margin: auto;
  }
  #searchPokemon{
    margin-bottom: 30px; 
  }
  .error{
    color: red;
    font-size: 150%;
  }
</style>
