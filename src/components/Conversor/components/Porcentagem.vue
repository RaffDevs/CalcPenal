<template>
    <div class="col-md-4 col-sm-12 text-center">
        <q-knob
        readonly
        v-model="value"
        show-value
        size="90px"
        :thickness="0.22"
        color="dark"
        track-color="grey-3"
        class="text-dark q-ma-md"
    >
        50%    
    </q-knob>
        <div class="text-bold text-h5">
            365
        </div>
    </div>
</template>

<script>
export default {
    
    data() {

        return {

            value : 50

        }

    },

}
</script>