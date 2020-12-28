<template>
    <q-card-section class="col-12 col-md-4" >

        <div class="text-h5 q-mt-sm q-mb-md">Calculo com datas e dias</div>

        <q-input color="dark" outlined bottom-slots v-model="textData" label="Data" stack-label type="date"/>

        <q-input color="dark" outlined bottom-slots v-model="textDias" type="number"  label="Dias" hint="">
            <template v-slot:append>
                <q-icon name="cancel" v-on:click="zeraDias" class="cursor-pointer" />
            </template>
        </q-input>
          
        <q-btn-toggle
        v-model="model"
        class="q-mb-md"
        no-caps
        rounded
        toggle-color="dark"
        color="white"
        text-color="dark"
        :options="[{value: 'one', slot : 'one'},{ value: 'two', slot : 'two'}]"
        >
            <template v-slot:one>
                <div v-on:click="addDias" class="row items-center no-wrap">
                <q-icon  name="add_circle" />
                </div>
            </template>

            <template v-slot:two>
              <div v-on:click="removeDias" class="row items-center no-wrap">
                <q-icon  name="remove_circle" />
              </div>
            </template>

        </q-btn-toggle>
          
        <q-btn-group push spread>
            <q-btn flat size="100" v-on:click='calculaData' label="Calcular" class="bg-dark" color="white" />
            <q-btn flat :label="resultado" color="dark" />
        </q-btn-group>

    </q-card-section>
</template>

<script>
export default {
    data() {

        return {
            //Declaração de variaveis
            textData: "",
            textDias: 0,
            resultado: "",

            model : 'one',
            
        }

    },
    methods:{
        //Função para adicionar dias
        addDias(){
            this.textDias++            
        },
        //Função para remover dias
        removeDias(){
            if(this.textDias > 0)
                this.textDias--          
        },
        //Função para zerar os dias
        zeraDias(){
            this.textDias = 0
        },

        //Função que soma data + dias
        calculaData(){
            this.resultado = this.addDays(this.textData, this.textDias)
        },
        //Função que adiciona os dias para o calculaData()
        addDays(date, days) {
            //Primeiro eu faço a soma da data com os dias
            console.log(result.getDate() + parseInt(days))
            result.setDate(result.getDate() + parseInt(days))
            console.log(result)

            //Agora eu faço uma formatação boba na mão pois o vue nao aceita tipo date, so string e int
            let dias = result.getDate()
            let mes = result.getMonth()  < 9 ? '0' + result.getMonth() + 1 : result.getMonth() + 1
            let ano = result.getFullYear()
            return dias + '/' + mes + '/' + ano
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
