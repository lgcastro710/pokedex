<template>
  <div
    class="fixed z-10 inset-0 overflow-y-auto"
    aria-labelledby="modal-title"
    role="dialog"
    aria-modal="true"
  >
    <div
      class="
        flex
        items-end
        justify-center
        min-h-screen
        pt-4
        px-4
        pb-20
        text-center
        sm:block
        sm:p-0
      "
    >
      <div
        class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"
        aria-hidden="true"
      ></div>
      <span
        class="hidden sm:inline-block sm:align-middle sm:h-screen"
        aria-hidden="true"
        >&#8203;</span
      >
      <div
        class="
          inline-block
          align-bottom
          bg-white
          rounded-none
          text-left
          overflow-hidden
          shadow-xl
          transform
          transition-all
          sm:my-8
          sm:align-middle
          sm:max-w-lg
          sm:w-full
          w-full
          modal-xs
        "
      >
        <div class="bg-white relative w-full" :style="bgColorClass">
          <BgCard :floorColor="floorColor"></BgCard>
          <div
            class="
              sm:flex
              sm:items-center
              absolute
              w-full
              top-0
              mt-7
              flex
              justify-center
              items-center
            "
          >
            <div class="mt-3 text-center sm:mt-0 sm:ml-4 sm:text-left">
              <h3
                class="
                  text-lg
                  leading-6
                  font-medium
                  text-gray-900
                  absolute
                  capitalize
                  title-modal
                "
                :style="colorTextClass"

                id="modal-title"
              >
                {{ data.name }}
              </h3>
              <div>
                <img
                  :src="data.imageUrl"
                  @load="processImage"
                  class="img-modal"
                />
              </div>
            </div>
          </div>
        </div>
        <div
          class="
            flex
            flex-row-reverse
            bg-gray-50
            px-4
            py-3
            sm:px-6
            sm:flex sm:flex-row-reverse
            justify-between
            items-center
          "
        >
          <button v-on:click.prevent="onClose" class="btn-close-modal">
            <i class="fa fa-close"></i>
          </button>
          <div style="display: flex">
            <PokePower
              v-for="(power, key) in data.types"
              v-bind:key="key"
              :type="power.type.name"
            ></PokePower>
          </div>
          <div>
            <p class="text-black">
              Altura:<span class="font-bold ml-2">{{ data.height }}</span>
            </p>
            <p class="text-black">
              Peso:<span class="font-bold ml-4">{{ data.weight }}</span>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BgCard from "./BgCard";
import Vibrant from "node-vibrant";
import PokePower from "./PokePower";

export default {
  name: "Modal",
  props: {
    onClose: Function,
    data: Object || String,
  },
  data() {
    return {
      bgColorClass: {},
      colorTextClass: {},
      bgLightMuted: {},
      floorColor: "",
    };
  },
  components: {
    BgCard,
    PokePower,
  },
  methods: {
    async processImage(e) {
      try {
        const imgTest =
          "https://cors-anywhere.herokuapp.com/" + e.target.currentSrc;
        Vibrant.from(imgTest).getPalette((err, palette) => {
          const colorSelected = "Vibrant";
          this.bgColorClass = { backgroundColor: palette[colorSelected].hex };
          this.colorTextClass = {
            backgroundColor: palette.DarkMuted.hex,
            color: palette.DarkMuted.titleTextColor,
            border: `2px solid ${palette.DarkMuted.hex}`,
          };
          this.bgLightMuted = {
            backgroundColor: palette.LightMuted.hex,
          };
          this.floorColor = palette.DarkVibrant.hex;
        });
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>
<style>

  .title-modal{
    color: rgb(255, 255, 255);
    padding-top: 15px;
    padding-bottom: 15px;
    border-radius: 0px 100px 100px 2px;
    top: 20px;
    left: -2px;
    width: auto;
    padding-left: 22px;
    padding-right: 25px;
    border-left: 0;
  }
  .img-modal{
    width: 330px;
    margin-top: 100px
  }
  .btn-close-modal{
    width: 20px;
    height: 20px;
    border: 2px solid #ed5565;
    background: #ed5565a3;
    border-radius: 5px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .btn-close-modal:hover{
    box-shadow: #ed5565 1px 1px 14px;
  }
  .btn-close-modal i{
    font-size: 17px;
    color: #ffffff;
  }

  @media (max-width: 600px) {
 .img-modal{
   margin-top: 0;
 }
    .title-modal{
      margin-top: -30px;
    }
    .modal-xs{
      position: absolute;
      top: 120px;
      width: 80%;
    }
  }
</style>
