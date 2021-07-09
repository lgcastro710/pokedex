<template>
  <div class="col-12">
    <div>
      <img
        src="../assets/poke-logo.png"
        style="width: 380px; margin: AUTO; min-height: 140px"
      />
    </div>
    <div class="flex p-4">
      <input
        type="text"
        class="search-input"
        v-model="txtBuscar"
        placeholder="Buscar"
      />
    </div>
    <div class="p-4">
      <FilterPower :power="power" :setPower="setPower"></FilterPower>
    </div>
    <Modal v-if="item" :onClose="onClose" :data="item"></Modal>
    <ul class="flex" style="flex-wrap: wrap">
      <LisItem
        v-for="(item, key) in listaFiltrada"
        v-bind:key="key"
        :item="item"
        :setItem="setItem"
      ></LisItem>
    </ul>
  </div>
</template>
<script>
import LisItem from "./ListItem";
import Modal from "./ui/Modal";
import FilterPower from "./FilterPower";
export default {
  name: "List",
  props: {
    lista: Array,
  },
  components: {
    LisItem,
    Modal,
    FilterPower,
  },
  data: function () {
    return {
      txtBuscar: "",
      power: "",
      item: null,
      active: "",
    };
  },
  computed: {
    listaFiltrada: function () {
      let arreglo = this.lista;
      const consulta = this.txtBuscar;
      if (consulta !== "") {
        arreglo = this.lista?.filter((pokemon) => {
          const name = pokemon.name;
          const id = String(pokemon.id);
          return (
            (name.toLowerCase() + " " + id.toLowerCase()).indexOf(
              consulta.toLowerCase()
            ) > -1
          );
        });
      } else if (this.power !== "") {
        arreglo = [];
        this.lista?.filter((pokemon) => {
          const type = pokemon.types.find(
            (type) => type.type.name === this.power
          );
          console.log("....", type);
          if (type) {
            arreglo.push(pokemon);
          }
        });
      }
      return arreglo;
    },
  },
  methods: {
    setPower: function (power) {
      this.txtBuscar = "";
      if (this.power === power) {
        this.power = "";
      } else {
        this.power = power;
      }
    },
    setItem: function (item) {
      console.log("item", item);
      this.item = item;
    },
    onClose: function () {
      this.item = null;
    },
  },
};
</script>
<style>
input {
  background-color: rgb(0 0 0 / 68%) !important;
  border-radius: 10px !important;
  border: solid 3px #4776fa !important;
}
h2,
input,
p {
  font-family: "Acme", sans-serif !important;
  color: white;
  font-size: 20px;
}
.search-input {
  width: 100%;
  border: 0;
  padding: 19px 10px;
  outline: none;
  text-align: center;
}
</style>
