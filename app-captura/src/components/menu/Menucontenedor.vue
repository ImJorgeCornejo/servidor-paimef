<template>
    <div class="barraMenu">
        <div class="slogan">
            <p>Plataforma de Transparencia</p>
        </div>
        <div class="usuario">
            <p>Morelos</p>
            <span>Cerrar Sesión</span>
        </div>
    </div>
</template>

<script>
export default {
    name:'Menucontenedor'
}
</script>

<style scoped>
    .barraMenu{
        width:100%;
        height:75px;
        background-color: #392f5c;
        color: #fff;
        display:flex;
    }
    .slogan{
        width:50%;
        display:flex; align-items:center; justify-content:flex-start;
        padding:0 30px;
        font-size: 24px;
        font-weight:400;
        text-transform:uppercase;
    }
    .usuario{
        width:50%;
        display: flex; flex-direction:column; align-items:flex-end; justify-content:center;
        padding:0 30px;
    }
    .usuario p{
        margin:0;
        font-size:22px;
        text-transform:uppercase;
    }
    .usuario span{
        font-size: 12px;
        cursor: pointer;
    }
    .usuario span:hover{
        text-decoration:underline;
    }
    
</style>