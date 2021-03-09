<template>
    <div class="capturar-info-general">
        <h1>Captura de Info General</h1>
        <div class="menu-captura-informacion">
            <div class="menu-captura-informacion-regresar">
                 <router-link to="/"><p>Regresar</p></router-link>
            </div>
           <div class="menu-captura-informacion-vertientes">
                <p @click="vertienteA" :class="activoVA">Vertiente A</p>
                <p @click="vertienteB" :class="activoVB">Vertiente B</p>
                <p @click="vertienteC" :class="activoVC">Vertiente C</p>
                <p @click="general">General</p>
                <p @click="resumen">Resumen</p>
           </div>
        </div>
        <RecursoFinanciero  :sectionTitle="infoVertiente" v-if="showVertientes"></RecursoFinanciero>
        <RecursoFinanciero  :sectionTitle="infoVertiente" v-if="false"></RecursoFinanciero>
        <RecursoFinanciero  :sectionTitle="infoVertiente" v-if="false"></RecursoFinanciero>
        <General :titulo="tituloGeneral" v-if="!showVertientes"></General>
    </div>
</template>

<script>
import RecursoFinanciero from '@/components/RecursoFinanciero.vue'
import General from '@/components/General.vue'
export default {
    components: {
        RecursoFinanciero,
        General
    },
    data() {
        return {
            infoVertiente:{
                mensaje: 'Recursos Financieros Vertiente',
                vertiente: 'A'
            },
            activoVA: '',
            activoVB: '',
            activoVC: '',
            showVertientes: true,
            tituloGeneral: 'Esto es información General'
        }
    },
    created(){
        this.vertienteA()
    },
    methods:{
        vertienteA(){
            this.infoVertiente.mensaje = 'Recursos Financieros Vertiente'
            this.infoVertiente.vertiente = 'A'
            this.activoVA = 'activar'
            this.activoVB = ''
            this.activoVC = ''
            this.showVertientes = true
        },
        vertienteB(){
            this.infoVertiente.vertiente = 'B'
            this.infoVertiente.mensaje = 'Recursos Financieros Vertiente'
            this.activoVA = ''
            this.activoVB = 'activar'
            this.activoVC = ''
        },
        vertienteC(){
            this.infoVertiente.vertiente = 'C'
            this.infoVertiente.mensaje = 'Recursos Financieros Vertiente'
            this.activoVB = ''
            this.activoVA = ''
            this.activoVC = 'activar'

        },
        general(){
            this.infoVertiente.mensaje = 'Recursos Financieros Generales'
            this.infoVertiente.vertiente = ''
            this.showVertientes = false

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
    .activar{
        color: #392f5c;
        font-weight: bold;
        text-transform:uppercase;
        border-bottom:3px solid #392f5c;
    }
</style>