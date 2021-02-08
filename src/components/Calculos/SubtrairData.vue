<template>
    <q-card-section class="col-12 col-md-6">
        <div class="text-h5 text-uppercase q-mt-sm q-mb-md">Subtrair Datas</div>
        <q-banner  dense rounded class="bg-dark text-white text-bold q-mb-md">
        Calcule a diferença entre duas data.
        </q-banner>
        <q-input color="dark" outlined bottom-slots v-model="date1" label="Data 1" stack-label type="date"/>

        <q-input color="dark" outlined bottom-slots v-model="date2" label="Data 2" stack-label type="date"/>
        
        <q-btn-group push spread>
            <q-btn flat size="100" label="Calcular" v-on:click="calculaData" class="bg-dark" color="white" />
            <q-btn @click="clipBoard" flat :label="resultado" color="dark" />
        </q-btn-group>
        
    </q-card-section>
</template>

<script>

import { copyToClipboard } from 'quasar';

export default {

    data() {
        return {
            //Declaração de variaveis
            date1: "",
            date2: "",
            resultado: ""

        }

    },
    methods:{

        //Calculo da Data
        calculaData(){
            this.resultado = "" 
            let data1 = new Date(this.date1)
            let data2 = new Date(this.date2)
            if(data1 < data2){
                this.resultado = "A Data 1 não pode ser menor que a data 2"
            }else if(data1 == data2){
                this.resultado = "A Data 1 não pode ser menor que a data 2"
            }else{
                let resultTime = Math.abs(data1.getTime() - data2.getTime());
                let resultDays = Math.ceil(resultTime / (1000 * 3600 * 24))
                this.resultado = resultDays + ' dias';
            }
            
        },

        clipBoard : function() {

            copyToClipboard(this.resultado).then(() => {

                this.$root.$emit('openClipboardModal');

            })

        }
    }
    
}
</script>