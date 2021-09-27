<template>
  <div id="app">
    <label>Search Pokemon:</label>
    <input type="text" v-model="search" placeholder="Search Pokemon" />
    <HelloWorld :pokemonList="filteredPokeList" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  data() {
    return {
      search: "",
      pokemonList: [],
    };
  },
  created() {
    this.loadPokeList();
  },
  methods: {
    async fetchPokeList() {
      try {
        const res = await fetch(
          "https://pokeapi.co/api/v2/pokemon/?limit=151&offset=0"
        );
        const data = await res.json();
        console.log(data);
        this.pokemonList = data.results;
        localStorage.setItem("pokemonList", JSON.stringify(this.pokemonList));
      } catch (error) {
        console.log(error);
      }
    },
    loadPokeList() {
      const localList = localStorage.getItem("pokemonList");
      if (!localList) {
        this.fetchPokeList();
      } else {
        this.pokemonList = JSON.parse(localList);
      }
    },
  },
  computed: {
    filteredPokeList() {
      return this.pokemonList.filter((pokemon) => {
        return pokemon.name.toLowerCase().includes(this.search.toLowerCase());
      });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
