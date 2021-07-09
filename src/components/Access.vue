<template>
  <div class="bg-access w-full flex items-end">
    <router-link to="/store" class="w-full flex justify-center"
      ><button class="btn-access">Yo Te Elijo!!</button></router-link
    >
  </div>
</template>

<style>
.bg-access {
  background-image: url("../assets/bg-access.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  width: 100%;
  min-height: 100vh;
  background-position: center;
}
.btn-access {
  background: #ed5565;
  border: 2px solid white;
  border-radius: 5px;
  cursor: pointer;
  padding: 10px;
  color: white;
  font-size: 20px;
  margin-bottom: 50px;
}
  .btn-access:hover{
    box-shadow: #ed5565 2px 2px 14px;
  }
</style>
