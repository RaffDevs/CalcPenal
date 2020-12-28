<template>
    <q-card-section class="col-12 col-md-4">
        <div class="text-h5 q-mt-sm q-mb-md">Subtrair Datas</div>

        <q-input color="dark" outlined bottom-slots v-model="date1" label="Data 1" stack-label type="date"/>

        <q-input color="dark" outlined bottom-slots v-model="date2" label="Data 2" stack-label type="date"/>
        
        <q-btn-group push spread>
            <q-btn flat size="100" label="Calcular" v-on:click="calculaData" class="bg-dark" color="white" />
            <q-btn flat :label="resultado" color="dark" />
        </q-btn-group>
        
    </q-card-section>
</template>

<script>
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
                    let result = new Date(data1.getTime() - data2.getTime())
                    this.resultado = result.getDate() + ' Dias'
                }
                
            },
    }
    
}
</script>