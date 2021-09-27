<template>
  <li class="card">
    <h3 class="pokemon">
      {{ pokemon.name }}
    </h3>
    <img :src="pokemonInfo.img"/>
    <p class="id">({{ pokemonInfo.id }})</p>
    <type-badge v-for="type in pokemonInfo.types" :key="type" :type="type"/>
  </li>
</template>
<script>
import TypeBadge from "./TypeBadge.vue"
export default {
  name: "PokemonCard",
  components:{TypeBadge},
  props: ["pokemon"],
  data() {
    return {
      pokemonInfo: {},
    };
  },
  created() {
    this.loadPokeInfo();
  },
  methods: {
    async fetchPokeInfo() {
      try {
        const res = await fetch(this.pokemon.url);
        const data = await res.json();
        console.log(data);
        this.pokemonInfo = {
            id: data.id,
            img: data.sprites.front_default,
            types: data.types.map(t => t.type.name),
        };
        localStorage.setItem(
          this.pokemon.name,
          JSON.stringify(this.pokemonInfo)
        );
      } catch (error) {
        console.log(error);
      }
    },
    loadPokeInfo() {
      const localInfo = localStorage.getItem(this.pokemon.name);
      if (!localInfo) {
        this.fetchPokeInfo();
      } else {
        this.pokemonInfo = JSON.parse(localInfo);
      }
    },
  },
};
</script>
<style scoped>
.card {
    list-style: none;
    border-radius: 7px;
    background-color: rgb(242, 242, 242);
    height: 250px;
    width: 200px;
    margin: 10px;
    transition: all ease 0.3s;
}
.card:hover {
    transform:translateY(-3px);

}
.id {
    font-size: 0.6rem;
    margin: 0 0 10px 0;
}
</style>