<template>
  <button
    v-on:click.prevent="onClick(data)"
    class="p-4 text-white font-bold hover:opacity-90"
    style="
      background-color: white;
      border: solid 5px black;
      border-radius: 50%;
      width: 30px;
      height: 30px;
      position: absolute;
    "
  >
    <span
      style="
        position: absolute;
        top: 6px;
        left: 6px;
        background-color: black;
        border-radius: 50%;
        width: 20px;
        height: 20px;
        display: inline-block;
      "
    ></span>
    <slot></slot>
  </button>
</template>
<script>
export default {
  name: "Button",
  props: {
    title: String,
    onClick: Function,
    data: Object || String,
  },
};
</script>