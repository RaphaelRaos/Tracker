<template>
  <header>
    <h1><img src="../assets/logo.png" alt="" sizes="" srcset="" /></h1>
    <button class="button" @click="changeTheme">{{ textButton }}</button>
  </header>
</template>
<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "SideBar",
  emits: ["aoTemaAlterado"],
  data() {
    return {
      modoEscuroAtivo: false,
    };
  },
  computed: {
    textButton() {
      if (this.modoEscuroAtivo) {
        return "Ativar Modo Claro";
      }
      return "Ativar Modo Escuro";
    },
  },
  methods: {
    changeTheme() {
      this.modoEscuroAtivo = !this.modoEscuroAtivo;
      this.$emit("aoTemaAlterado", this.modoEscuroAtivo);
    },
  },
});
</script>
<style scoped>
header {
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  padding: 1rem;
  text-align: center;
}
img {
  width: 60%;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>