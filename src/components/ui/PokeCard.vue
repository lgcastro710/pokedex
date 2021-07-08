<template>
  <div
    class="p-4 box-border shadow-lg overflow-hidden"
    style="
      transition: 0.5s;
      box-shadow: 1px 1px 14px #611405;
      border-radius: 50px;
    "
  >
    <slot></slot>
  </div>
</template>
<script>
export default {
  name: "Card",
};
</script>