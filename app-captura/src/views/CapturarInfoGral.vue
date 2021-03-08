<template>
    <div class="capturar-info-general">
        <h1>Captura de Info General</h1>
        <div class="menu-captura-informacion">
            <div class="menu-captura-informacion-regresar">
                 <router-link to="/"><p>Regresar</p></router-link>
            </div>
           <div class="menu-captura-informacion-vertientes">
                <p @click="vertienteA">Vertiente A</p>
                <p @click="vertienteB">Vertiente B</p>
                <p @click="vertienteC">Vertiente C</p>
                <p @click="general">General</p>
                <p @click="resumen">Resumen</p>
           </div>
        </div>
        <RecursoFinanciero :sectionTitle="infoVertiente"></RecursoFinanciero>
    </div>
</template>

<script>
import RecursoFinanciero from '@/components/RecursoFinanciero.vue'
export default {
    components: {
        RecursoFinanciero
    },
    data() {
        return {
            infoVertiente:{
                mensaje: 'Recursos Financieros Vertiente',
                vertiente: 'A'
            }
        }
    },
    methods:{
        vertienteA(){
            this.infoVertiente.mensaje = 'Recursos Financieros Vertiente'
            this.infoVertiente.vertiente = 'A'
        },
        vertienteB(){
            this.infoVertiente.vertiente = 'B'
            this.infoVertiente.mensaje = 'Recursos Financieros Vertiente'
        },
        vertienteC(){
            this.infoVertiente.vertiente = 'C'
            this.infoVertiente.mensaje = 'Recursos Financieros Vertiente'
        },
        general(){
            this.infoVertiente.mensaje = 'Recursos Financieros Generales'
            this.infoVertiente.vertiente = ''

        },
        resumen(){
            this.infoVertiente.mensaje = 'Resumen de la información'
            this.infoVertiente.vertiente = ''
        }
    }
}
</script>

<style scoped>

    .capturar-info-general h1{
        text-align:center;
    }
    .menu-captura-informacion{
        width:90%;
        display:flex;
        margin:0 auto;
    }
    .menu-captura-informacion-regresar{
        width:50%;
    }
    .menu-captura-informacion-vertientes{
        width:50%;
        display:flex; justify-content: space-evenly;
        font-size:12px;
    }
    .menu-captura-informacion-vertientes p{
        cursor:pointer;
    }
    .menu-captura-informacion-vertientes p:hover{
        text-decoration:underline;
    }
</style>