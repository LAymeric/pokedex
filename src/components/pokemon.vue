<template>
  <div class="pokemon">
        <h3>{{this.pokemon.name }}</h3>
  </div>
</template>
<script>
export default {
   props: ['pokemon']
};
</script>