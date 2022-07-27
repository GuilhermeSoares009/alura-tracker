<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de tarefa.">
                <input type="text" name="" id="" class="input" placeholder="Qual tarefa você deseja iniciar?">
            </div>
            <div class="column">
                <div class="is-flex is-align-items-center is-justify-content-space-between">
                        <Cronometro :tempoEmSegundos="tempoEmSegundos"/> <!-- Passando o tempoEmSegundos como propriedade -->
                        <button class="button" @click="iniciar">
                            <span class="icon">
                                <i class="fas fa-play"></i>
                            </span>
                            <span>play</span>
                        </button>
                        <button class="button" @click="finalizar">
                            <span class="icon">
                                <i class="fas fa-stop"></i>
                            </span>
                            <span>stop</span>
                        </button>
                </div>
 
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Cronometro from './Cronometro.vue';
export default defineComponent({
    name: 'Formulario',
    data()
    {
        return {
            tempoEmSegundos: 0,
            cronometro: 0
        }
    },
    components: {
        Cronometro
    },
    methods:{
        iniciar() {
            // começa a contagem
            // 1 seg  = 1000 ms
            this.cronometro =  setInterval(() => {
                this.tempoEmSegundos +=1;
            }, 1000);
        },
        finalizar()
        {
            // finaliza a contagem
            clearInterval(this.cronometro);
        }


    }
})
</script>