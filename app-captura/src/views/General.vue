<template>
    <div class="info-general">
        <div class="general-titulo">
             <h3>Información General</h3>
             <div class="general-titulo-botones">
                 <router-link to="/">Regresar</router-link>
                 <router-link to="/captura/info-general">Capturar Información</router-link>
             </div>
        </div>
       <div class="general-body">
           <h3>Consultar Información</h3>
           <div class="general-body-periodo">
                <OpcionPeriodo></OpcionPeriodo>
           </div>
           <div class="general-body-mostrarInfo">

           </div>
           
       </div>
        
    </div>
</template>

<script>

import OpcionPeriodo from '@/components/OpcionPeriodo.vue'
export default {
    components:{
        OpcionPeriodo
    }
}
</script>

<style scoped>
    .info-general{
        width:100%;
    }
    .general-titulo{
        width:70%;
        margin:20px auto;
        text-align:center;
    }
    .general-titulo h3{
        font-size:30px;
    }
    .general-titulo-botones{
        width:40%;
        height:40px;
        margin:0 auto;
        display:flex; align-items:center; justify-content:space-evenly;
    }
    .general-body{
        width:95%;
        background-color: #f1f1f2;
        margin:20px auto;
    }
    .general-body h3{
        padding-top:30px;
        text-align:center;
    }
</style>