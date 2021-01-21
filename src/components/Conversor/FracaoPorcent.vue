<template>
    <q-card-section class="col-md-8 q-pa-none" >
        <div class="text-h5  q-mt-sm q-mb-md">FRAÇÃO E PORCENTAGEM</div>
        <q-banner  dense rounded class="bg-dark text-white text-bold q-mb-md">
        Converta os dias em frações e porcentagens.
        </q-banner>
        <q-card-section class="row">
            <div class="col-12 flex justify-end items-center">
                <q-input  style="width : 200px" color="dark" type="number"  v-model="diasInput" label="Dias" hint="">
                    <template v-slot:append>
                    <q-icon name="cancel" @click="diasInput = '0'" class="cursor-pointer" />
                    </template>
                </q-input>
                <q-btn @click="calcula" flat label="Calcular" class="bg-dark q-ml-md" style="width : 100px; height : 40px" color="white" />
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
                        <q-carousel
                            v-model="slideFracao"
                            transition-prev="jump-right"
                            transition-next="jump-left"
                            animated
                            control-color="dark"
                            padding
                            arrows
                            height="350px"
                            class="col-12 rounded-borders desktop-only"
                            @transition="calcula"
                        >
                            <q-carousel-slide name="1" class="no-wrap flex-center">
                            <div class="q-mt-md text-center row justify-center">
                                <Fracao fracao="1/6" :valor="dias"/>
                                <Fracao fracao="1/5" :valor="dias"/>
                                <Fracao fracao="1/4" :valor="dias"/>
                                <Fracao fracao="1/3" :valor="dias"/>
                            </div>
                            </q-carousel-slide>
                            <q-carousel-slide name="2" class="no-wrap flex-center">
                            <div class="q-mt-md text-center row justify-center">
                                <Fracao fracao="3/8" :valor="dias"/>
                                <Fracao fracao="2/5" :valor="dias"/>
                                <Fracao fracao="5/12" :valor="dias"/>
                                <Fracao fracao="11/24" :valor="dias"/>
                            </div>
                            </q-carousel-slide>
                            <q-carousel-slide name="3" class="no-wrap flex-center">
                            <div class="q-mt-md text-center row justify-center">
                                <Fracao fracao="1/2" :valor="dias"/>
                                <Fracao fracao="3/5" :valor="dias"/>
                                <Fracao fracao="2/3" :valor="dias"/>
                            </div>
                            </q-carousel-slide>
                            
                        </q-carousel>
                        <!-- Cards de fração no mobile -->
                        <Fracao class="mobile-only" fracao="1/6" :valor="dias"/>
                        <Fracao class="mobile-only" fracao="1/5" :valor="dias"/>
                        <Fracao class="mobile-only" fracao="1/4" :valor="dias"/>
                        <Fracao class="mobile-only" fracao="1/3" :valor="dias"/>
                        <Fracao class="mobile-only" fracao="3/8" :valor="dias"/>
                        <Fracao class="mobile-only" fracao="2/5" :valor="dias"/>
                        <Fracao class="mobile-only" fracao="5/12" :valor="dias"/>
                        <Fracao class="mobile-only" fracao="11/24" :valor="dias"/>
                        <Fracao class="mobile-only" fracao="1/2" :valor="dias"/>
                        <Fracao class="mobile-only" fracao="3/5" :valor="dias"/>
                        <Fracao class="mobile-only" fracao="2/3" :valor="dias"/>
                    
                    </q-tab-panel>
                    <q-tab-panel name="porcentagem" class="row justify-center" >
                    <q-carousel
                            v-model="slidePorcent"
                            transition-prev="jump-right"
                            transition-next="jump-left"
                            animated
                            control-color="dark"
                            padding
                            arrows
                            height="300px"
                            class="col-12 rounded-borders desktop-only"
                            @transition="calcula"
                        >
                            <q-carousel-slide name="1" class="no-wrap flex-center">
                            <div class="q-mt-md text-center row justify-center">
                                <Porcentagem :porcentagem="16" :valor="dias"/>
                                <Porcentagem :porcentagem="20" :valor="dias"/>
                                <Porcentagem :porcentagem="25" :valor="dias"/>
                                <Porcentagem :porcentagem="30" :valor="dias"/>
                            </div>
                            </q-carousel-slide>
                            <q-carousel-slide name="2" class="no-wrap flex-center">
                            <div class="q-mt-md text-center row justify-center">
                                <Porcentagem :porcentagem="40" :valor="dias"/>
                                <Porcentagem :porcentagem="50" :valor="dias"/>
                                <Porcentagem :porcentagem="60" :valor="dias"/>
                                <Porcentagem :porcentagem="70" :valor="dias"/>
                            </div>
                            </q-carousel-slide>
                        </q-carousel>
                        <!-- Cards de porcentagem no mobile -->
                        <Porcentagem class="mobile-only" :porcentagem="16" :valor="dias"/>
                        <Porcentagem class="mobile-only" :porcentagem="20" :valor="dias"/>
                        <Porcentagem class="mobile-only" :porcentagem="25" :valor="dias"/>
                        <Porcentagem class="mobile-only" :porcentagem="30" :valor="dias"/>
                        <Porcentagem class="mobile-only" :porcentagem="40" :valor="dias"/>
                        <Porcentagem class="mobile-only" :porcentagem="50" :valor="dias"/>
                        <Porcentagem class="mobile-only" :porcentagem="60" :valor="dias"/>
                        <Porcentagem class="mobile-only" :porcentagem="70" :valor="dias"/>
                    </q-tab-panel>
                </q-tab-panels>
            </div>
        </q-card-section>
    </q-card-section>
</template>

<script>

import Fracao from './components/Fracao';

import Porcentagem from './components/Porcentagem';

import { copyToClipboard } from 'quasar';


export default {

    components : {

        Fracao,

        Porcentagem

    },
    
    data() {

        return {

            dias : "0",

            diasInput : "0",

            tab : 'fracao',

            slideFracao : "1",

            slidePorcent : "1"

        }

    },

    methods : {

        calcula : function() {

            this.dias = this.diasInput;

        },

        clipBoard : function() {

            copyToClipboard(this.resultado).then(() => {

                this.$root.$emit('openClipboardModal');

            })

        }

    },


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

