<template>
  <div class="container mx-auto">
    <!-- <router-link to="/"><button>volver</button></router-link> -->
    <div class="flex p-4 flex-col md:flex-row">
      <div class="box-border" style="width: 100%">
        <List :lista="lista"></List>
      </div>
    </div>
  </div>
</template>

<script>
import List from "./List";

const data = [
  {
    clave: "07028a40-5c5f-4762-b07b-39bfea40abfc",
    descripcion: "Texto de prueba",
    imageUrl: "https://assets.pokemon.com/assets/cms2/img/pokedex/full/007.png",
    nombre: "Pokemon 1",
    id: "1",
  },
  {
    clave: "15f099a0-7b12-46d7-b284-ead55d3f87f6",
    descripcion: "Texto de prueba",
    imageUrl: "https://assets.pokemon.com/assets/cms2/img/pokedex/full/010.png",
    nombre: "Pokemon 2",
    id: "2",
  },
  {
    clave: "98ed1c9e-6a63-4416-b4a5-76862d74a9aa",
    descripcion: "Texto de prueba",
    imageUrl: "https://assets.pokemon.com/assets/cms2/img/pokedex/full/002.png",
    nombre: "Pkemon 3",
    id: "3",
  },
  {
    clave: "c84a0c5b-406a-4c29-ae79-bf3b499218bd",
    descripcion: "Texto de prueba",
    imageUrl: "https://assets.pokemon.com/assets/cms2/img/pokedex/full/005.png",
    nombre: "Pokemon 4",
    id: "4",
  },
  {
    clave: "d0094eec-1cf3-45bc-9a4d-3e16ed63e249",
    descripcion: "Texto de prueba",
    imageUrl: "https://assets.pokemon.com/assets/cms2/img/pokedex/full/063.png",
    nombre: "Pokemon 5",
    id: "5",
  },
  {
    clave: "f0e81670-5b56-4724-88f6-d61de5395065",
    descripcion: "Texto de prueba",
    imageUrl: "https://assets.pokemon.com/assets/cms2/img/pokedex/full/012.png",
    nombre: "Pokemon 6",
    id: "6",
  },
];

export default {
  name: "Container",
  components: {
    List,
  },
  data: () => ({
    lista: data,
  }),
  methods: {
    created: function () {
      this.listarElementos();
    },
  },
};
</script>