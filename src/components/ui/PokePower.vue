<template>
  <div class="sprite" :class="type"></div>
</template>

<script>
export default {
  name: "Power",
  props: {
    type: String,
  },
};
</script>
<style>
.sprite {
  background: url("../../assets/sprite.png") no-repeat;
  background-size: 280px;
  width: 35px;
  height: 35px;
  border-radius: 50%;
  margin: 2px;
}
</style>