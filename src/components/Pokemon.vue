<template >
  <div>
    <div class='row'>
      <div class='col-5'>
        <h2><b>{{this.pokemon.name }}</b> -  <span class="badge badge-secondary">#{{this.pokemon.id}}</span></h2>
      </div>
    </div>
    <div class='row'>
      <div class='col-5'>
        <img v-bind:src="this.pokemon.sprites.front_default" width=150 height=150/>
      </div>
      <div class='col-6'>
        <h4><b>Type: </b></h4><br>
          <p v-for="type in this.pokemon.types" v-bind:type="type.name" v-bind:key="type.name">{{type.type.name}}</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Pokemon',
  props: ['pokemon'],
  data () {
    return {
      pokemonDetails: null
    }
  }
}
</script>
<style>
</style>
