<template>
    <q-dialog v-model="dialog" seamless position="right"  @hide="dialog = false">
      <Calculadora/>
    </q-dialog>
</template>

<script>

import Calculadora from './Calculadora';

export default {

    components : {

        Calculadora

    },

    mounted() {

        this.$root.$on('openCalculatorModal', () => this.dialog = !this.dialog);

    },

    data() {

        return {

            dialog : false

        }

    }
    
}
</script>

<style lang="scss">

    

</style>