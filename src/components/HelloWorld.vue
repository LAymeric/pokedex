<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
     <pokemon v-for="poke in info.data.results" :pokemon="poke"/>
  </div>
</template>

<script>
import axios from 'axios';
import pokemon from './pokemon';

export default {
  name: 'HelloWorld',
  components: { pokemon },
  data () {
    return {
      msg: 'test',
      info:{
        data :{
          results :[]
        }
      }
    }
  },
  mounted () {
    axios
      .get('https://pokeapi.co/api/v2/pokemon/?limit=150')
      .then(response => (this.info = response))
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
