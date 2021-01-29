<template>
    <q-dialog v-model="show" @hide="show = false" persistent transition-show="scale" transition-hide="scale">
      <q-card class="bg-dark text-white" style="width: 300px">
        <q-card-section>
          <div class="text-h6">Erro ao validar senha de autenticação!</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
            Não encontramos o codigo para a validação!
            Caso deseje receber o código, clique no botão abaixo para acessar o site
            e cadastrar seu email na sessão <b>"Obtenha nossa Calculadora de Execução Penal".</b>
        </q-card-section>

        <q-card-actions align="right" class="bg-dark text-white">
          <q-btn outline label="Receber Código" @click="goToSite" />
        </q-card-actions>
      </q-card>
    </q-dialog>
</template>

<script>
export default {

    created() {

        this.$root.$on('showValidator', () => this.show = true);

    },
    
    data() {

        return {

            show : false

        }

    },

    methods : {

        goToSite : function() {

            window.location.href = 'https://criminalistaemfoco.com.br/home/#/'

        }

    }

}
</script>