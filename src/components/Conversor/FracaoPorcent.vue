<template>
    <q-card-section class="col-md-8 q-pa-none">
        <q-card-section class="row">
            
            <div class="col-12 flex justify-end items-center">
                <q-input style="width : 200px" color="dark" type="number"  v-model="text" label="Dias" hint="">
                    <template v-slot:append>
                    <q-icon name="cancel" @click="text = ''" class="cursor-pointer" />
                    </template>
                </q-input>
                <q-btn flat label="Calcular" class="bg-dark q-ml-md" style="width : 100px; height : 40px" color="white" />
            </div>

            <div class="col-12">
                <q-tabs
                v-model="tab"
                dense
                class="text-grey"
                active-color="dark"
                indicator-color="dark"
                align="justify"
                narrow-indicator>
                    <q-tab name="fracao" label="Fração" />
                    <q-tab name="porcentagem" label="Porcentagem" />
                </q-tabs>

                <q-separator />

                <q-tab-panels v-model="tab" animated>
                    <q-tab-panel name="fracao" class="row justify-center" >
                    <Fracao/>
                    <Fracao/>
                    <Fracao/>
                    <Fracao/>
                    <Fracao/>
                    <Fracao/>
                    </q-tab-panel>
                    <q-tab-panel name="porcentagem" class="row justify-center" >
                    <Porcentagem/>
                    <Porcentagem/>
                    <Porcentagem/>
                    <Porcentagem/>
                    </q-tab-panel>
                </q-tab-panels>
            </div>
        </q-card-section>
    </q-card-section>
</template>

<script>

import Fracao from './components/Fracao';

import Porcentagem from './components/Porcentagem';

export default {

    components : {

        Fracao,

        Porcentagem

    },
    
    data() {

        return {

            tab : 'fracao',

            slide : 1

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

