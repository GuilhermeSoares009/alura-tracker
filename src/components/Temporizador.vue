<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <!-- Passando o tempoEmSegundos como propriedade -->
    <Cronometro :tempoEmSegundos="tempoEmSegundos" />
    <!-- Criando botões componente de botões -->
    <Botao @clicado="iniciar" texto="play" icone="fas fa-play" :desabilitado="cronometroRodando"/>
    <Botao @clicado="finalizar" texto="stop" icone="fas fa-stop" :desabilitado="!cronometroRodando"/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Cronometro from './Cronometro.vue';
import Botao from './Botao.vue';

export default defineComponent({
    name: 'Temporizador',
    emits:['aoTemporizadorFinalizado'],
    data()
    {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false,
        }
    },
    components: {
        Cronometro,
        Botao
    },
    methods:{
        iniciar() {
            // começa a contagem
            // 1 seg  = 1000 ms
            this.cronometroRodando = true;
            this.cronometro =  setInterval(() => {
                this.tempoEmSegundos +=1;
            }, 1000);
        },
        finalizar()
        {
            // finaliza a contagem
            this.cronometroRodando = false;
            clearInterval(this.cronometro);
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
            this.tempoEmSegundos = 0;
        }


    }
})
</script>