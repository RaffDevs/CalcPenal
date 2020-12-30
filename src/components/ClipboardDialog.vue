<template>
  <q-dialog v-model="seamless" auto-close seamless position="top" @hide="seamless = false">
      <q-card style="width: 350px">
        <q-card-section class="row items-center no-wrap">
          Valor copiado para área de tranferência.
        </q-card-section>
      </q-card>
    </q-dialog>
</template>


<script>
export default {

    created() {

        this.$root.$on('openClipboardModal', () => this.seamless = true)

    },

    data () {

        return {

            seamless: false

        }

    }

}
</script>