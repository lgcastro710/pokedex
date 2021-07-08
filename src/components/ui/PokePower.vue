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