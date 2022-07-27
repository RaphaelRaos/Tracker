<template>
  <Caixa>
    <div class="columns">
      <div class="column is-7">{{ tasks.description || 'Tarefa sem Descrição' }}</div>
      <div class="column">
        <Cronometro :timeInSecond="tasks.duracaoEmSegundos" />
      </div>
    </div>
  </Caixa>
</template>

<script lang="ts">
import ITasks from "@/interfaces/ITasks";
import { defineComponent, PropType } from "vue";
import Caixa from "./Boxes.vue";
import Cronometro from "./Stopwatch.vue";

export default defineComponent({
  name: "Tasks",
  components: {
    Cronometro,
    Caixa
  },
  props: {
    tasks: {
      type: Object as PropType<ITasks>,
      required: true,
    },
  },
});
</script>

<style scoped>

</style>