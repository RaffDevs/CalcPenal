<template>
  <div class=" mobile-only">
    <q-layout view="hHh Lpr lff" style="height: 300px" class="shadow-2 rounded-borders">
      <q-drawer
        v-model="drawer"
        show-if-above
        :width="200"
        :breakpoint="500"
        bordered
        content-class="bg-grey-3"
      >
        <q-img class="absolute-top bg-dark"  style="height: 180px">
          <div class="absolute-bottom bg-transparent">
            <h5 class="text-h5">Calculadora Execução Penal</h5>    
          </div>
        </q-img>
        <q-list padding style="margin-top: 180px;">
          <q-expansion-item
            expand-separator
            icon="change_circle"
            label="Conversor"
          >
            <template v-for="(menuItem, index) in menuList">
                <q-item  v-if="menuItem.type === 'conversor'" :key="index" @click="setActive(menuItem.label)" :active="menuItem.label === activeItem" clickable v-ripple>
                    <q-item-section avatar>
                    <q-icon class="" :name="menuItem.icon" />
                    </q-item-section>
                    <q-item-section class="">
                    {{ menuItem.label }}
                    </q-item-section>
                </q-item>
            </template>
          </q-expansion-item>

          <q-expansion-item
            expand-separator
            icon="calculate"
            label="Calculos"
          >
          <template v-for="(menuItem, index) in menuList">
              <q-item v-if="menuItem.type === 'calculos'" :key="index" @click="setActive(menuItem.label)" :active="menuItem.label === activeItem" clickable v-ripple>
                  <q-item-section avatar>
                  <q-icon class="" :name="menuItem.icon" />
                  </q-item-section>
                  <q-item-section class="">
                  {{ menuItem.label }}
                  </q-item-section>
              </q-item>
              
            </template>
          </q-expansion-item>
                
        </q-list>
      
        
      </q-drawer>

      <q-page-container>
        <q-page class="q-pa-md row justify-center q-gutter-md" padding>
          <DiasAnos v-if="activeItem === 'Anos para dias'" style="width : 100%"/>
          <FracaoPorcent v-if="activeItem === 'Fração/Porcent'"/>
          <DataDias v-if="activeItem === 'Datas e dias'"/>
          <SubtrairData v-if="activeItem === 'Subtrair Datas'"/>
        </q-page>
      </q-page-container>
    </q-layout>
  </div>
</template>

<script>

import DiasAnos from '../components/Conversor/DiasAnos';

import FracaoPorcent from '../components/Conversor/FracaoPorcent';

import DataDias from '../components/Calculos/DataDias';

import SubtrairData from '../components/Calculos/SubtrairData';

export default {

  components : {

    DiasAnos,

    FracaoPorcent,

    DataDias,

    SubtrairData

  },
    
  data (){

      return {

          drawer: false,

          menuList : [

            {label : 'Anos para dias', icon : 'remove', type : 'conversor'},

            {label : 'Fração/Porcent', icon : 'remove', type : 'conversor'},

            {label : 'Datas e dias', icon : 'remove', type : 'calculos'},

            {label : 'Subtrair Datas', icon : 'remove', type : 'calculos'},

          ],

          activeItem : 'Anos para dias'



      }

  },

    mounted() {

        this.$root.$on('changeDrawer', () => this.drawer = !this.drawer);

    },

    methods : {

      setActive : function($event) {

        this.activeItem = $event;

      }

    },

}
</script>
