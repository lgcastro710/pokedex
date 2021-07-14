<template>
  <div class="bg-access w-full flex items-center" style="">
    <img
            src="../assets/poke-logo.png"
            class="logo-access"
    />
    <div style="width: 100%; text-align: center">
      <img src="../assets/poke222.png" class="img-access" />
    </div>
    <div style="
    width: 100%;
    text-align: center;
    position: absolute;
    bottom: 10%;
    background-color: rgb(0 0 0 / 54%);
">
      <h1 class="title">Yo Te Elijo!!</h1>
      <router-link to="/store" class="w-full flex justify-center" style="
">
        <button class="btn-access">
          <img      src="../assets/pokebola.png" style="width: 120px; margin: auto" />
        </button></router-link
      >
    </div>
  </div>
</template>
<style>
  .title{
    margin: 0;
    color: white;
    font-family: "Acme", sans-serif !important;
    font-size: 50px;
  }
  .bg-access {
    width: 100%;
    min-height: 100vh;
    justify-content: end; flex-direction: column
  }
  .img-access {
    width: 70%; margin: auto
  }
  .logo-access{
    width: 380px;
    min-height: 140px
  }
  .btn-access {
    order: 0;
    border-radius: 50%;
    cursor: pointer;
    color: white;
    font-size: 20px;
    margin: 0 10px 10px;
    font-family: "Acme", sans-serif !important;
    position: relative;
    padding: 0;
    display: inline-block;
  }
  .btn-access:hover{
    box-shadow: #ed5565 2px 2px 14px;
  }
  @media (max-width: 600px) {
    .logo-access{
      width: 90%;
      min-height: auto
    }
    .img-access {
      width: 100%; margin: auto
    }
  }
</style>
