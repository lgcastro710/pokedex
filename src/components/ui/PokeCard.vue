<template>
  <div
    class="p-4 box-border shadow-lg overflow-hidden card-animation"
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

<style>
.card-animation:hover {
  animation: pokeCardAnimation 0.5s ease-out;
}
@keyframes pokeCardAnimation {
  0% {
    transform: rotate(0deg);
  }

  25% {
    transform: rotate(3deg);
  }

  75% {
    transform: rotate(-3deg);
  }

  100% {
    transform: rotate(0deg);
  }
}
</style>