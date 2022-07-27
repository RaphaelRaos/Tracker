<template>
  <button class="button" @click="clicado" :disabled="desabilitado">
    <span class="icon"> <i :class="icone"></i></span>
    <span>{{ text }}</span>
  </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "ButtonButton",
  emits: ['clicado'],
  props: {
    desabilitado: {
      type: Boolean,
    },
    icone: {
      type: String,
      required: true,
    },
    text: {
      type: String,
      required: true,
    },
  },
  methods: {
    clicado (): void {
      this.$emit('clicado');
    },
  },
});
</script>
