<template>
  <section>
    <strong class="display">{{ tempoDecorrido }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "Cronometro",
  props:{
    tempoEmSegundos: {
        type: Number,
        default: 0 
    }
  },
  computed: {
    tempoDecorrido(): string {
      return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11, 8); // Pega o formato HH:MM:SS
      // E também no date ele multiplica por mil o tempo para trabalhar em milissegundos.
    },
  },
});
</script>
<style scoped>
  .display {
    color: var(--texto-primario);
  }
</style>