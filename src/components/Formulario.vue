<template>
  <div class="box formulario">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="description"
        />
        <!--v-model: Linka com o estado do objeto a descrição da tarefa.-->
      </div>
      <div class="column">
        <Timer @whenStopTimer="finishTask" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Timer from "@/components/Timer.vue";

export default defineComponent({
  name: "FormularioVue",
  emits: ["atSaveTasks"],
  components: {
    Timer,
  },
  data() {
    return {
      description: "",
    };
  },
  methods: {
    finishTask(elipsedTime: number): void {
      this.$emit("atSaveTasks", {
        duracaoEmSegundos: elipsedTime,
        description: this.description,
      });
      this.description = "";
    },
  },
});
</script>

<style>
.formulario {
  color: var(--text-primary);
  background-color: var(--bg-primary);
}
</style>

