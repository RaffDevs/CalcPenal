<template>
    <q-card-section class="col-12 col-md-6" >

        <div class="text-h5  q-mt-sm q-mb-md">DATAS E DIAS</div>
        <q-banner  dense rounded class="bg-dark text-white text-bold q-mb-md">
        Some ou subtraía dias de uma data.
        </q-banner>
        <q-input color="dark" outlined bottom-slots v-model="textData" label="Data" stack-label type="date"/>

        <q-input color="dark" outlined bottom-slots v-model="textDias" type="number"  label="Dias" hint="">
            <template v-slot:append>
                <q-icon name="cancel" v-on:click="zeraDias" class="cursor-pointer" />
            </template>
        </q-input>
        <div class="q-mb-sm">
            *Selecione o tipo do cálculo
        </div>
        <q-btn-toggle
        v-model="operacao"
        class="q-mb-md"
        no-caps
        rounded
        toggle-color="dark"
        color="white"
        text-color="dark"
        :options="[{value: 'adiciona', slot : 'one'}, { value: 'subtrai', slot : 'two'}]"
        >
            <template v-slot:one>
                <div class="row items-center no-wrap">
                    <div>Somar</div>
                <q-icon right name="add_circle" />
                </div>
            </template>

            <template v-slot:two>
              <div  class="row items-center no-wrap">
                  <div>Subtrair</div>
                <q-icon right name="remove_circle" />
              </div>
            </template>

        </q-btn-toggle>
          
        <q-btn-group push spread>
            <q-btn flat size="100" v-on:click='calculaData' label="Calcular" class="bg-dark" color="white" />
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
            textData: "",
            textDias: 0,
            resultado: "",


            operacao : 'adiciona',
            
        }

    },
    methods:{
    
        //Função para zerar os dias
        zeraDias(){
            this.textDias = 0
        },

        //Função que adiciona os dias para o calculaData()
        calculaData : function() {

            //Pego a data do input e crio uma string valida de tempo para passa dentro do objeto Date
            let data = new Date(`${this.textData}T00:00:00`);

            let dataComputada;

            if (this.operacao === 'adiciona') {

                // Adiciona dias na data selecionada
                dataComputada = data.setDate(data.getDate() + Number(this.textDias));

            } else {
                
                // Subtrai dias da data selecionada
                dataComputada = data.setDate(data.getDate() - Number(this.textDias));

            };

            let dia = new Date(dataComputada).getDate() <= 9 ? '0' + new Date(dataComputada).getDate() : new Date(dataComputada).getDate();

            let mes = new Date(dataComputada).getMonth() + 1 <= 9 ?  `0${new Date(dataComputada).getMonth() + 1}` : new Date(dataComputada).getMonth() + 1;

            let ano = new Date(dataComputada).getFullYear();

            this.resultado = `${dia}/${mes}/${ano}`;

        },

        clipBoard : function() {

            copyToClipboard(this.resultado).then(() => {

                this.$root.$emit('openClipboardModal');

            })

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


