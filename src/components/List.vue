<template>
  <div class="col-12">
    <div class="flex p-4">
      <input
        type="text"
        class="search-input"
        v-model="txtBuscar"
        placeholder="Buscar"
      />
    </div>
    <Modal v-if="item" :onClose="onClose" :data="item"></Modal>
    <ul class="flex" style="flex-wrap: wrap">
      <LisItem
        v-for="(item, key) in listaFiltrada"
        v-bind:key="key"
        :item="item"
        :eliminar="eliminar"
        :setItem="setItem"
      ></LisItem>
    </ul>
  </div>
</template>
<script>
import LisItem from "./ListItem";
import Modal from "./ui/Modal";
export default {
  name: "List",
  props: {
    lista: Array,
    eliminar: Function,
  },
  components: {
    LisItem,
    Modal,
  },
  data: function () {
    return {
      txtBuscar: "",
      item: null,
    };
  },
  computed: {
    listaFiltrada: function () {
      let arreglo = this.lista;
      const consulta = this.txtBuscar;
      if (consulta !== "") {
        arreglo = this.lista?.filter(
          ({ nombre, descripcion, precio }) =>
            (
              nombre.toLowerCase() +
              " " +
              descripcion.toLowerCase() +
              " " +
              precio.toLowerCase()
            ).indexOf(consulta.toLowerCase()) > -1
        );
      }
      return arreglo;
    },
  },
  methods: {
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
  background-color: white !important;
  border-radius: 10px !important;
  border: solid 3px black !important;
}
h2,
input,
p {
  font-family: "Montserrat", sans-serif !important;
}
</style>