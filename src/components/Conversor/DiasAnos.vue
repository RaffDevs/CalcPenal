<template>
    <q-card-section class="col-md-4 col-sm-12">

        <q-select class="q-mb-lg" v-model="selectedOption" color="dark" :options="options" label="Converter de:" />

        <div v-if="selectedOption === 'Anos para dias'">
            <q-input color="dark" type="number" outlined bottom-slots v-model="text"  label="Anos">
                <template v-slot:append>
                    <q-icon name="cancel" @click="text = ''" class="cursor-pointer" />
                </template>
            </q-input>

            <q-input color="dark" type="number" outlined bottom-slots v-model="text"  label="Meses" hint="">
                <template v-slot:append>
                    <q-icon name="cancel" @click="text = ''" class="cursor-pointer" />
                </template>
            </q-input>

            <q-input color="dark" type="number" outlined bottom-slots v-model="text" label="Dias" hint="">
                <template v-slot:append>
                    <q-icon name="cancel" @click="text = ''" class="cursor-pointer" />
                </template>
            </q-input>
        </div>

        <div v-else-if="selectedOption === 'Dias para anos'">
            <q-input color="dark" outlined bottom-slots v-model="text"  label="Dias">
                <template v-slot:append>
                    <q-icon name="cancel" @click="text = ''" class="cursor-pointer" />
                </template>
            </q-input>
        </div>

       
        <q-btn-group push spread>
            <q-btn flat size="100" label="Calcular" class="bg-dark" color="white" />
            <q-btn flat label="6325" color="dark" />
        </q-btn-group>
        
    </q-card-section>
</template>


<script>
export default {

    data() {
        
        return {

            options : [

            'Anos para dias',

            'Dias para anos'

            ],

            selectedOption : 'Anos para dias'

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


