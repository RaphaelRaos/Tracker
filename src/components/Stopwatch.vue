<template>
  <section>
    <strong class="display">
      {{ timeElapsed }}
    </strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Stopwatch",
  //PROPS => PROPRIEDADES QUE VAMOS RECEBER DOS COMPONENTES PAIS
  props: {
      timeInSecond:{
          type: Number,
          default: 0
      }
  },
  // COMPUTED => MONITORA AS INFORMAÇÕES E A CADA ATUALIZAÇÃO ELE VAI REAGIR E ALTERAR O OBJETO
  computed: {
    timeElapsed(): string {
      return new Date(this.timeInSecond * 1000).toISOString().substr(11, 8);
    },
  },
});
</script>

<style>
.display{
  color: var(--text-primary);
  background-color: var(--bg-primary);
}
</style>