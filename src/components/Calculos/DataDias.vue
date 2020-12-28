<template>
    <q-card-section class="col-12 col-md-4" >

        <div class="text-h5 q-mt-sm q-mb-md">Calculo com datas e dias</div>

        <q-input color="dark" outlined bottom-slots v-model="text" label="Data" stack-label type="date"/>

        <q-input color="dark" outlined bottom-slots v-model="text" type="number"  label="Dias" hint="">
            <template v-slot:append>
                <q-icon name="cancel" @click="text = ''" class="cursor-pointer" />
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
                <div class="row items-center no-wrap">
                <q-icon  name="add_circle" />
                </div>
            </template>

            <template v-slot:two>
              <div class="row items-center no-wrap">
                <q-icon  name="remove_circle" />
              </div>
            </template>

        </q-btn-toggle>
          
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

            model : 'one',
            
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
