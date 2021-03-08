<template>
    <div class="barraMenu">
        <a href="http://paimeftransparente.com" target="_blank">PAIMEF Transparente</a>
        <a href="#">Asistencia técnica</a>
    </div>
</template>

<script>
export default {
    name: 'BarraMenu'
}
</script>

<style scoped> 
    .barraMenu{
        height:30px;
        background-color:#cc9933;
        display: flex; align-items:center; justify-content: space-between;
        padding:0 30px;
        font-size:12px;
    }
    .barraMenu p{
        margin:0;
    }
    .barraMenu a{
       margin:0;
    }
</style>