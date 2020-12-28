<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="bg-dark">
        <q-btn flat @click="drawerSetter" round dense icon="menu" class="mobile-only"/>
        <q-toolbar-title >
          Calc Penal
        </q-toolbar-title>
      </q-toolbar>
    </q-header>
    <q-page-container>
      <Desktop/>
      <Mobile/>
      <q-page-sticky position="bottom-right" :offset="[50, 18]">
            <q-btn fab out icon="calculate" color="dark"  label=""/>
      </q-page-sticky>
    </q-page-container>
  </q-layout>
</template>

<script>

import Desktop from '../pages/Desktop';

import Mobile from '../pages/Mobile';

export default {

  components : {

    Desktop,

    Mobile

  },

  data() {

    return {

      changeDrawer : false

    }

  },

  methods : {

    drawerSetter : function() {

      this.$root.$emit('changeDrawer');

    }

  }
  
}
</script>
