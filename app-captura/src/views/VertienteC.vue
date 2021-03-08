<template>
    <div class="info-vertiente">
        <div class="vertiente-titulo">
             <h3>Vertiente C</h3>
             <p>Atención</p>
             <div class="vertiente-titulo-botones">
                 <router-link to="/">Regresar</router-link>
                 <router-link to="/captura/vertiente-c">Capturar Información</router-link>
             </div>
        </div>
       <div class="vertiente-body">
           <h3>Información</h3>
           <div class="vertiente-body-periodo">
                <OpcionPeriodo></OpcionPeriodo>
           </div>
           <div class="vertiente-body-mostrarInfo">

           </div>
           
       </div>
        
    </div>
</template>

<script>

import OpcionPeriodo from '@/components/OpcionPeriodo.vue'
export default {
    components: {
        OpcionPeriodo
    }
}
</script>

<style scoped>
     .info-vertiente{
        width:100%;
    }
    .vertiente-titulo{
        width:70%;
        margin:20px auto;
        text-align:center;
    }
    .vertiente-titulo h3{
        font-size:30px;
    }
    .vertiente-titulo-botones{
        width:40%;
        height:40px;
        margin:0 auto;
        display:flex; align-items:center; justify-content:space-evenly;
    }
    .vertiente-body{
        width:95%;
        background-color: #f1f1f2;
        margin:20px auto;
    }
    .vertiente-body h3{
        padding-top:30px;
        text-align:center;
    }
</style>