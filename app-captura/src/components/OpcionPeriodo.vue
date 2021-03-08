<template>
<div class="contenedor-opcion-periodo">
    <p>Periodo</p>
    <select id="opcionPeriodo" name="opcionPeriodo">
        <option value="">Selecciona un periodo</option>
    </select>
    <button>Conultar</button>
</div>
</template>

<script>
export default {
    name:"OpcionPeriodo",
    data() {
        return {
           
        }
    },
}
</script>
<style scoped>
    .contenedor-opcion-periodo{
        width:40%;
        margin:10px auto;
        display:flex; align-items:center; justify-content:space-evenly;
        padding-bottom:40px;
    }
</style>