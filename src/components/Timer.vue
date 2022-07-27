<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
      <!-- Quando adicionamos ":" na frente da propriedade no VUE, relacionamos ela ao estado (Data)-->
    <Stopwatch :timeInSecond="timeInSecond" />    
    <ButtonButton @clicado="start" icone="fas fa-play" text="play" :desabilitado="stopwatchInFunction"/>
    <ButtonButton @clicado="finish" icone="fas fa-stop" text="stop" :desabilitado="!stopwatchInFunction"/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Stopwatch from "@/components/Stopwatch.vue";
import ButtonButton from "@/components/ButtonButton.vue";

export default defineComponent({
  name: "Timer",
  //LISTA DE EVENTOS QUE UM COMPONENTE É CAPAZ DE EMITIR
  emits:['whenStopTimer'],
  
  //DATA => LOCAL PARA DEFINIR O ESTADO INICIAL DOS NOSSOS OBJETOS * É UM METODO*
  data() {
    return {
      timeInSecond: 0,
      stopwatch: 0,
      stopwatchInFunction: false,
    };
  },
  components: {
    Stopwatch,
    ButtonButton
  },
  methods: {
    start() {
      this.stopwatchInFunction = true;
      this.stopwatch = setInterval(() => {
        this.timeInSecond += 1;
      }, 1000);
    },
    finish() {
      this.stopwatchInFunction = false;
      clearInterval(this.stopwatch);
      this.$emit('whenStopTimer',this.timeInSecond)
      this.timeInSecond = 0
    },
  },
});
</script>
