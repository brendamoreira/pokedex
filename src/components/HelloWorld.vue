<template>
  <div class="hello">
    <ul>
      <pokemon-card v-for="pokemon in pokemonList" :key="pokemon.name" :pokemon="pokemon"/>
    </ul>
  </div>
</template>

<script>
import PokemonCard from "./PokemonCard.vue";
export default {
  name: "HelloWorld",
  components: { PokemonCard },
  props: ["pokemonList"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
a {
  color: #42b983;
}
</style>
