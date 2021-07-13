<template>
  <div
    class="container mx-auto"
    v-if="lista.length"
    :handleScroll="handleScroll"
  >
    <div class="px-8">
      <router-link to="/"
        ><button class="btn-volver">Volver</button></router-link
      >
    </div>
    <div class="flex p-4 flex-col md:flex-row">
      <div class="box-border" style="width: 100%">
        <PokeList :lista="lista"></PokeList>
      </div>
    </div>
  </div>
</template>

<script>
import PokeList from "./PokeList";
import axios from "axios";

export default {
  name: "Container",
  components: {
    PokeList,
  },
  data: () => ({
    lista: [],
    offset: 0,
  }),
  methods: {
    listarElementos: async function () {
      const pokeData = await axios
        .get(
          `https://pokeapi.co/api/v2/pokemon?limit=${
            this.lista.length ? 10 : 20
          }&offset=${this.offset}`
        )
        .then((response) => response.data.results);
      pokeData.forEach(async (pokeInfo) => {
        const pokemon = await axios
          .get(pokeInfo.url)
          .then((response) => response.data);
        let imgId = pokemon.id;
        if (pokemon.id < 10) {
          imgId = "00" + pokemon.id;
        }
        if (pokemon.id > 9 && pokemon.id < 100) {
          imgId = "0" + pokemon.id;
        }
        pokemon.imageUrl = `https://assets.pokemon.com/assets/cms2/img/pokedex/detail/${imgId}.png`;
        this.lista.push(pokemon);
      });
    },
    handleScroll() {
      window.onscroll = () => {
        const scrollTop = parseInt(
          Math.ceil(document.documentElement.scrollTop)
        );

        const innerHeight = window.innerHeight;
        const offsetHeight = document.documentElement.offsetHeight;

        const bottomOfWindow = scrollTop + innerHeight === offsetHeight;
        console.log(
          bottomOfWindow,
          parseInt(scrollTop.toFixed(0)),
          innerHeight,
          offsetHeight
        );
        if (bottomOfWindow) {
          this.offset += 10;
          this.listarElementos();
        }
      };
    },
  },
  created: function () {
    this.listarElementos();
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  },
};
</script>
<style>
.btn-volver {
  background: rgb(0 0 0 / 68%);
  border: solid 3px #014e9e;
  width: 50px;
  margin-top: 10px;
  padding: 5px;
  color: white;
  font-size: 10px;
  border-radius: 5px;
  margin-top: 10px;
}
.btn-volver:hover {
  box-shadow: rgb(21 123 255) 1px 1px 14px;
}
</style>
