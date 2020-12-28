<template>
    <q-card-section class="col-md-4 col-sm-12">

        <q-select class="q-mb-lg" v-model="selectedOption" color="dark" :options="options" label="Converter de:" />

        <div v-if="selectedOption === 'Anos para dias'">
            <q-input color="dark" type="number" outlined bottom-slots v-model="textAnos"  label="Anos">
                <template v-slot:append>
                    <q-icon name="cancel" @click="textAnos = ''" class="cursor-pointer" />
                </template>
            </q-input>

            <q-input color="dark" type="number" outlined bottom-slots v-model="textMeses"  label="Meses" hint="">
                <template v-slot:append>
                    <q-icon name="cancel" @click="textMeses = ''" class="cursor-pointer" />
                </template>
            </q-input>

            <q-input color="dark" type="number"  outlined bottom-slots v-model="textDias" label="Dias" hint="">
                <template v-slot:append>
                    <q-icon name="cancel" @click="textDias = ''" class="cursor-pointer" />
                </template>
            </q-input>
        </div>

        <div v-else-if="selectedOption === 'Dias para anos'">
            <q-input color="dark" outlined bottom-slots v-model="textDiasAnos"  label="Dias">
                <template v-slot:append>
                    <q-icon name="cancel" @click="textDiasAnos = ''" class="cursor-pointer" />
                </template>
            </q-input>
        </div>

       
        <q-btn-group push spread>
            <q-btn flat size="100" v-on:click='calculaData' label="Calcular" class="bg-dark" color="white" />
            <q-btn flat :label="resultado" color="dark"/>
        </q-btn-group>
        
    </q-card-section>
</template>


<script>
export default {

    data() {
        return {
            //Declaração de variaveis
            textAnos: "",
            textMeses: "",
            textDias: "", 
            resultado: "",
            textDiasAnos: "",

            

            options : [

            'Anos para dias',

            'Dias para anos'

            ],

            selectedOption : 'Anos para dias',

        }

    },
    methods:{
            //Calculo da Data
            calculaData(){
                this.resultado = "" 
                //Este if é baseado no que vem selecionado no dropdown
                if(this.selectedOption == 'Anos para dias'){
                    let anos = 365 * this.textAnos
                    let meses = 30 * this.textMeses
                    let dias = parseInt(this.textDias)
                    this.resultado = (anos + meses + dias)
                }else{
                    this.resultado = this.getFormatedStringFromDays(parseInt(this.textDiasAnos))
                }
            },

            //Funcao que serve para transformar dias em uma data composta DD/MM/AA
            getFormatedStringFromDays(numberOfDays) {
                let years = Math.floor(numberOfDays / 365)
                let months = Math.floor(numberOfDays % 365 / 30)
                let days = Math.floor(numberOfDays % 365 % 30)
                //Formatação em String
                let yearsDisplay = years > 0 ? years + (years == 1 ? " Ano, " : " Anos, ") : ""
                let monthsDisplay = months > 0 ? months + (months == 1 ? " Mes, " : " Meses, ") : ""
                let daysDisplay = days > 0 ? days + (days == 1 ? " Dia" : " Dias") : ""
                return yearsDisplay + monthsDisplay + daysDisplay
            }
    }
    
}
</script>


<style lang="scss">
    input[type="number"]::-webkit-outer-spin-button, 
    input[type="number"]::-webkit-inner-spin-button {
        -webkit-appearance: none;
        margin: 0;
    }

    input[type=number] {
        -moz-appearance:textfield;
    }
</style>


