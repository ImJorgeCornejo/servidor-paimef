<template>
  <div class="home">
    <div class="infoGeneral">
      <h1>Info General</h1>
      <p>Información General</p>
      <router-link to="/info-general"> <p class="btnInicio">Mostrar</p></router-link>
    </div>
    <div class="vertienteA">
      <h1>Vertiente A</h1>
      <p>Profesionalización</p>
      <router-link to="/vertiente-a"> <p class="btnInicio">Mostrar</p></router-link>
    </div>
    <div class="vertienteB">
      <h1>Vertiente B</h1>
      <p>Prevención</p>
      <router-link to="/vertiente-b"> <p class="btnInicio">Mostrar</p></router-link>
    </div>
    <div class="vertienteC">
      <h1>Vertiente C</h1>
      <p>Atención</p>
     <router-link to="/vertiente-c"> <p class="btnInicio">Mostrar</p></router-link>
    </div>
    
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'Home'
  
}
</script>

<style scoped>
  .home{
    width:95%;
    height:600px;
    margin:25px auto;
    background-color: #fff;
    border-radius:10px;
    display:flex; align-items:center; justify-content:space-evenly;
  }
  .infoGeneral{
    background-color: #9D1D96;
    padding:30px;
    border-radius:10px;
    color: #fff;
    text-align:center;
  }
  .vertienteA{
    background-color: #ECB016;
    padding:30px;
    border-radius:10px;
    color: #fff;
    text-align:Center;
  }
  .vertienteB{
    background-color: #84BAAC;
    padding:30px;
    border-radius:10px;
    color: #fff;
    text-align:center;
  }
  .vertienteC{
    background-color: #392F5C;
    padding:30px;
    border-radius:10px;
    color: #fff;
    text-align:center;
  }
  .btnInicio{
    width:70%;
    margin:0 auto;
    background-color: #20A4AC;
    padding:10px 0;
    cursor:pointer;
  }
</style>