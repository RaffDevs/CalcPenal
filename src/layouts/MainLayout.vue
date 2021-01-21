<template>
  <q-layout view="lHh Lpr lFf">
    <ModalCalc/>
    <ClipboardDialog/>
    <q-header elevated>
      <q-toolbar class="bg-dark">
        <q-btn flat @click="drawerSetter" round dense icon="menu" class="mobile-only"/>
        <q-toolbar-title >
          CRIMINALISTA EM FOCO | <small>Calculadora de Execução Penal</small>
        </q-toolbar-title>  
      </q-toolbar>
    </q-header>
    <q-page-container>
      <Desktop/>
      <Mobile/>
      <q-page-sticky  position="bottom-right" :offset="[50, 18]">
            <q-btn fab out icon="fas fa-calculator" color="dark" @click="modalCalculadora"/>
      </q-page-sticky>
    </q-page-container>
  </q-layout>
</template>

<script>

import Desktop from '../pages/Desktop';

import Mobile from '../pages/Mobile';

import ModalCalc from '../components/Calculadora/ModalCalc';

import ClipboardDialog from '../components/ClipboardDialog';

export default {

  components : {

    Desktop,

    Mobile,

    ModalCalc,

    ClipboardDialog

  },

  data() {

    return {

      changeDrawer : false

    }

  },

  methods : {

    drawerSetter : function() {

      this.$root.$emit('changeDrawer');

    },

    modalCalculadora : function() {

      this.$root.$emit('openCalculatorModal');

    }

  }
  
}
</script>
