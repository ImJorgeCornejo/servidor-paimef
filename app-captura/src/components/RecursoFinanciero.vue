<template>
    <div class="recurso-financiero">
        <div class="agregar-informacion">
            <div class="contenido-agregar-informacion">
                <div class="formulario-contenido-agregar-informacion">
                    <form @submit.prevent="calculo(accion.recursoHumano,accion.recursoFinanciero)" id="formulario-info">
                        <label for="accion">Acción</label>
                        <input type="text" id="accion" v-model="accion.accion">
                        <label for="accion">Recurso Humano</label>
                        <input type="number" id="recursoHumano" v-model.number="accion.recursoHumano">
                        <label for="accion">Recurso Material</label>
                        <input type="number" id="recursoMaterial" v-model.number="accion.recursoFinanciero">
                        <button :disabled="btnDisabled">Agregar</button>
                    </form>
                    <div class="total-info">
                        <h2 v-if="mostrarTotal"><span>Total: </span>$ {{totalParcial}} </h2>
                        <button v-if="btnGuardar" @click="guardarAcciones" class="btnGuardarAccion">Guardar Acciones</button> 
                    </div>
                    <p :class="mensajeAlerta" v-if="alertaValidacion">{{alertaTexto}}</p>
                </div>
            </div>
        </div>
        <div class="mostrar-informacion">
            <div class="contenido-mostrar-informacion">
                <p class="titulo-contenido-agregar-informacion">{{sectionTitle.mensaje}} <span> {{ sectionTitle.vertiente}}</span></p>
               <table class="info-general-table">
                   <thead>
                       <tr>
                           <th>Acción</th>
                           <th>Recurso Humano</th>
                           <th>Recurso Material</th>
                           <th>Total Recurso</th>
                           <th>Funciones</th>
                       </tr>
                   </thead>
                   <tbody>
                       <tr  v-for="(accion,index) in totalAccion" :key="index">
                           <td class="table-text-uppercase">{{accion.accion}}</td>
                           <td>$ {{accion.humano}}</td>
                           <td>$ {{accion.financiero}}</td>
                           <td>$ {{accion.totalRecurso}}</td>
                           <td class="btn-funciones">
                               <p @click="editarAccion">Editar</p>
                               <p @click="eliminarAccion">Eliminar</p>
                           </td>
                       </tr>
                   </tbody>

               </table>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:'RecursoFinanciero',
    props:['sectionTitle'],
    data() {
        return {
            btnDisabled: false,
            alertaValidacion: false,
            btnGuardar: false,
            mensajeAlerta:'',
            alertaTexto: '',
            mensajeTitulo: 'Recurso Financiero Vertiente A',
            accion:{
                accion:'',
                recursoHumano: '',
                recursoFinanciero: '',
                totalRecurso:''
            },
            totalParcial:0,
            totalAccion:[],
            totalVertienteA:[],
            totalVertienteB:[],
            totalVertienteC:[],
            saveVA:null,
            saveVB:null,
            saveVC:null,
            mostrarTotal: false

        }
    }, 
    methods:{
        calculo(humano,financiero){

            if(this.accion.accion === '' || this.accion.recursoHumano === '' || this.accion.recursoFinanciero === ''){
                this.alertaTag(true,'alertaDanger','Todos los campos son obligatorios')
                return
            }
            this.accion.totalRecurso = parseInt(humano) + parseInt(financiero);

            const accion = { 
                accion: this.accion.accion,
                humano: String(this.accion.recursoHumano),
                financiero: String(this.accion.recursoFinanciero),
                totalRecurso: String(this.accion.totalRecurso)
            }

            this.totalParcial = this.totalParcial + this.accion.totalRecurso
            this.btnGuardar = true;

            this.mostrarTotal = true

            this.seleccionarVertiente(accion)
            this.alertaTag(true,'alertaSuccess','¡Acción agregada!')
            
        },
        alertaTag(validacion,estilo,texto){
            this.alertaValidacion = validacion
            this.mensajeAlerta = estilo
            this.alertaTexto = texto
            setTimeout(() => {
                    this.alertaValidacion = false
                }, 2000);
        },
        seleccionarVertiente(accion){
            const vertiente = this.sectionTitle.vertiente;
            if(vertiente === 'A'){
                this.totalVertienteA.push(accion)
                this.totalAccion = this.totalVertienteA
            }else if(vertiente === 'B'){
                this.totalAccion = []
               this.totalVertienteB.push(accion)
               this.totalAccion = this.totalVertienteB
            }else if(vertiente === 'C'){
                this.totalAccion = []
                this.totalVertienteC.push(accion) 
                this.totalAccion = this.totalVertienteC
            }
            this.limpiarFormulario()

        },
        limpiarFormulario(){
            this.accion.accion = ''
            this.accion.recursoHumano = ''
            this.accion.recursoFinanciero = ''
            this.accion.totalRecurso = ''
        },
        editarAccion(){
            console.log('editar acción')
        },
        eliminarAccion(){
            console.log('eliminar acción')
        },
        guardarAcciones(){
            const vertiente = this.sectionTitle.vertiente
            if(vertiente === 'A'){
                this.saveVA = this.totalParcial;
                this.totalAccion = []
                this.totalParcial = 0
                console.log(this.totalVertienteA)
                console.log(this.saveVA)
            }else if( vertiente === 'B'){
                this.saveVB = this.totalParcial;
                this.totalAccion = []
                this.totalParcial = 0
                console.log(this.totalVertienteB)
                console.log(this.saveVB)
            }else if( vertiente === 'C'){
                this.saveVC = this.totalParcial;
                this.totalAccion = []
                this.totalParcial = 0
                console.log(this.totalVertienteC)
                console.log(this.saveVC)
            }
        },
        test(){
            this.$emit('')
        }
    }
}
</script>


<style scoped>
    .recurso-financiero{
        width:95%;
        height:480px;
        background-color:#f0f0f0;
        display:flex;
        margin:10px auto;

    }
    .agregar-informacion{
        width:30%;
    }
    .mostrar-informacion{
        width:70%;
    }
    .contenido-mostrar-informacion{
        width:96%;
        height:450px;
        margin:15px auto;
        background-color: #ECECEC;
    }
    .info-general-table{
        width:95%;
        margin:10px auto;
    }
    .info-general-table td{
        text-align:center;
    }

    .contenido-agregar-informacion{
        width:90%;
        margin:10px auto;
    }
    .titulo-contenido-agregar-informacion{
        font-size:18px;
        font-weight: bold;
        padding:10px 12px;
    }
    .formulario-contenido-agregar-informacion form{
        display:flex; flex-direction: column;
        width:50%;
        margin:10px auto;
    }
    .formulario-contenido-agregar-informacion label{
        margin-top:20px;
        font-weight: bold;
    }
    .formulario-contenido-agregar-informacion input{
        height:24px;
        font-size:14px;
        text-align:right;
        text-transform:uppercase;
    }
    button{
        width:70%;
        margin:10px auto;
        height:30px;
        border:none;
        text-transform:uppercase;
        cursor:pointer;
    }
    button:hover{
        font-weight: bold;
        border:1px solid black;
    }
    button:disabled,button[disabled]{
        background-color:#ECECEC;
        color: #fff;
        cursor:no-drop;
    }
    .btn-generico{
        
        background-color:green;
        color:#fff;
        
    }
    .table-text-uppercase{
        text-transform:uppercase;
    }
    .btn-funciones{
        display:flex; justify-content: space-evenly;
        font-size:12px;
    }

    .alertaDanger{
        text-align:center;
        background-color:#F18A82;
        color:#fff;
        width:70%;
        margin:10px auto;
        padding:10px 15px;
    }
       .alertaSuccess{
        text-align:center;
        background-color:#82F1BC;
        color:#fff;
        width:70%;
        margin:10px auto;
        padding:10px 15px;
    }
    .total-info{
        width:100%;
        text-align:center;
    }
    .btnGuardarAccion{
        background-color: none;
    }
    
   

</style>