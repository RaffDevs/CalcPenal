<template>
    <div class="col-md-3 col-sm-12 text-center">
        <q-knob
        readonly
        v-model="porcentagem"
        show-value
        size="90px"
        :thickness="0.22"
        color="dark"
        track-color="grey-3"
        class="text-dark q-ma-md"
    >
        {{ porcentagem }}%
    </q-knob>
        <div class="text-bold text-h5">
            {{ result }} <small>dias</small>
        </div>
    </div>
</template>

<script>
export default {

    props : {

        porcentagem : Number,

        valor : String

    },

    created() {

        console.log('CRIOU PORCENTAGEM')

        this.result = Math.round(Number(this.valor) * this.porcentagem) / 100;

    },
    
    data() {

        return {

            result : 0

        }

    },

    watch : {

        valor : function() {

            this.result = Math.round(Number(this.valor) * this.porcentagem) / 100;

        }

    }

}
</script>