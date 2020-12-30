<template>
    <q-dialog v-model="dialog" seamless position="right"  @hide="this.dialog = false">
      <q-card style="width: 350px" bordered>
        <q-card-section class="row items-center">
            <q-card-section class="col-12">
                <q-input class="text-right" outlined disable v-model="text" label="0" />
            </q-card-section>
            <q-card-section class="col-12 row no-wrap justify-center" style="border : 1px solid red">
                <div class="col-3" style="margin : 0 2px">
                    <q-btn color="dark" label="9" style="width : 100%"/>
                </div>
                <div class="col-3 " style="margin : 0 2px">
                    <q-btn color="dark" label="9" style="width : 100%"/>
                </div>
                <div class="col-3 " style="margin : 0 2px">
                    <q-btn color="dark" label="9" style="width : 100%"/>
                </div>
                <div class="col-3 " style="margin : 0 2px">
                    <q-btn color="dark" label="9" style="width : 100%"/>
                </div>
            </q-card-section>
        </q-card-section>
      </q-card>
    </q-dialog>
</template>

<script>
export default {

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