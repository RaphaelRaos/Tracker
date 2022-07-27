<template>
  <main class="columns is-gapless is-multiline " :class="{'modo-escuro': modoEscuroAtivo}">
    <div class="column is-one-fifth">
      <SideBar @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-four-fifths conteudo">
      <FormularioVue @atSaveTasks="saveTasks" />
      <div class="lista">
        <Tasks
          v-for="(tarefa, index) in tarefas"
          :key="index"
          :tasks="tarefa"
        />
        <Boxes v-if="listIsEmpty"> Você está sem tarefas hoje :(</Boxes>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SideBar from "@/components/SideBar.vue";
import FormularioVue from "@/components/Formulario.vue";
import Boxes from "@/components/Boxes.vue";
import Tasks from "@/components/Tasks.vue";
import ITasks from "@/interfaces/ITasks";

export default defineComponent({
  name: "App",
  components: {
    SideBar,
    FormularioVue,
    Tasks,
    Boxes,
  },
  data() {
    return {
      tarefas: [] as ITasks[],
      modoEscuroAtivo: false,
    };
  },
  computed: {
    listIsEmpty(): boolean {
      return this.tarefas.length === 0;
    },
  },
  methods: {
    saveTasks(tarefas: ITasks) {
      this.tarefas.push(tarefas);
    },
    trocarTema(modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  },
});
</script>

<style>

.lista {
  padding: 1.25rem;
}
main {
  --bg-primary: #fff;
  --text-primary: #000;
}
main.modo-escuro{
  --bg-primary: #2b2d42;
  --text-primary: #ddd;
}

.conteudo{
  background-color: var(--bg-primary);
  color: var(--text-primary);
}
</style>
