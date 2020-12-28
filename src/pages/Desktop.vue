<template>
<div class="desktop-only">
    <q-page class="q-pa-md row justify-center q-gutter-md ">
      <q-card class="col-12"  flat bordered border>
        <q-item-section class="bg-dark text-white">
            <q-item-label>
              <q-icon name="calculate" size="30px"/>
              CONVERSOR
            </q-item-label>
        </q-item-section>
        <q-card-section class="row" >
            <DiasAnos/>
            <FracaoPorcent/>
        </q-card-section>
      </q-card>

      <q-card style="width : 100%; height : 450px" flat bordered border>
        <q-item-section class="bg-dark text-white">
            <q-item-label>
              <q-icon name="calculate" size="30px"/>
              CALCULOS
            </q-item-label>
            <q-item-label caption>
            </q-item-label>
          </q-item-section>
        <q-card-section class="row" >
          <DataDias/>
          <SubtrairData/>
        </q-card-section>
      </q-card>
  </q-page>
</div>

  

</template>

<script>

import DiasAnos from '../components/Conversor/DiasAnos';

import FracaoPorcent from '../components/Conversor/FracaoPorcent';

import DataDias from '../components/Calculos/DataDias';

import SubtrairData from '../components/Calculos/SubtrairData';

export default {

  name : 'Index',
  
  components : {

    DiasAnos,
    FracaoPorcent,
    DataDias,
    SubtrairData

  },

  data() {

    return {

    }

  },

}
</script>
