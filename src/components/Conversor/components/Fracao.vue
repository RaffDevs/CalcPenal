<template>
    <div  class="col-md-4 col-12 q-ma-sm">
        <q-card >
            <q-card-section class="bg-dark text-white">
                <div class="text-center text-bold">{{ fracao }}</div>
            </q-card-section>

            <q-card-actions class="text-h5" vertical align="center">
                {{result}}
            </q-card-actions>
        </q-card>
    </div>
</template>

<script>
export default {

    name : 'Fracao',

    props : {

        fracao : String,

        valor : String

    },

    created() {

        if (this.valor % this.denominador === 0) {

                this.result = Math.floor((this.valor / this.denominador) * this.numerador);
                
        } else {

            this.result = Math.floor((this.valor * this.numerador) / this.denominador);

        };

    },

    data() {

        return {

            result : 0,

            numerador : Number(this.fracao.split('/')[0]),

            denominador : Number(this.fracao.split('/')[1]),

        }
    },

    watch : {

        valor : function() {

            if (this.valor % this.denominador === 0) {

                this.result = Math.floor((this.valor / this.denominador) * this.numerador);
                
            } else {

                this.result = Math.floor((this.valor * this.numerador) / this.denominador);

            };

        }

    }

   
}
</script>