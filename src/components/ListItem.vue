<template>
  <li class="w-full p-4 md:w-1/3 lg:w-1/4" v-on:click.prevent="setItemSelected(item)">
    <PokeCard style="padding: 0" :class="bg" >
      <div class="card-body" style="position: relative">
        <h1 class="poke-title" v-if="bg === 'pokeBolaActive'">
          <span>#{{ item.id }} </span>
          {{ item.name }}
        </h1>
        <div class="flip" :class="rotate">
          <img
            src="../assets/pokebola.png"
            style="max-width: 200px; border-radius: 50%"
            class="flip-1"
          />
          <div
            class="flip-2"
            style="
              background-color: black;
              width: 200px;
              height: 200px;
              border-radius: 50%;
            "
          >
            <img :src="item.imageUrl" style="width: 100%; height: auto" />
          </div>
        </div>
      </div>
      <div class="card-footer">
        <Button
          v-if="bg === 'pokeBolaActive'"
          title="View"
          :onClick="setItemSelected"
          :data="item"
          class="btn-open-card"
        ></Button>
        <div style="display: flex">
          <PokePower
            v-for="(power, key) in item.types"
            v-bind:key="key"
            :type="power.type.name"
          ></PokePower>
        </div>
      </div>
    </PokeCard>
  </li>
</template>
<script>
import PokeCard from "./ui/PokeCard";
import Button from "./ui/Button";
import PokePower from "./ui/PokePower";

export default {
  name: "ListItem",
  data: () => ({
    rotate: "",
    bg: "pokeBolaInActive",
  }),
  props: {
    item: Object,
    setItem: Function,
  },
  components: {
    PokeCard,
    Button,
    PokePower,
  },
  methods: {
    rotatePokeBola: function () {
      setTimeout(() => {
        this.rotate = "flip-rotate";
        this.bg = "pokeBolaActive";
      }, 1500);
    },
    setItemSelected: function (item) {
      this.setItem(item);
    },
  },
  created: function () {
    this.rotatePokeBola();
  },
};
</script>
<style>
.card-body {
  height: 280px;
  margin-top: 12px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  border-bottom: solid 5px black;
  padding: 10px 0;
}

.card-footer {
  background-color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  min-height: 82px;
  position: relative;
}
.btn-open-card{
  top: -20px
}
.btn-open-card:hover{
  box-shadow: #000 2px 2px 14px;
}
.poke-title {
  font-family: "Acme", sans-serif !important;
  font-size: 25px !important;
  margin-top: -17px !important;
  color: #000000;
  text-transform: capitalize;
}
.flip {
  position: relative;
  top: 0;
  width: 100%;
  height: 100%;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: 0.5s;
  transform-style: preserve-3d;
}
.pokeBolaActive {
  background-color: #ed5565;
}
.pokeBolaInActive {
  background-color: #272323;
}
.flip-rotate {
  transform: rotateY(-180deg);
}
.flip-1,
.flip-2 {
  position: absolute;
  backface-visibility: hidden;
}
.flip-2 {
  transform: rotateY(-180deg);
}
</style>
