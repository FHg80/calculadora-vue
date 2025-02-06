<script setup>
  import { reactive } from 'vue';


  const estado = reactive({
    numeroA: 0,
    numeroB: 0,
    operacao: '',
    resultado: 0
  })

  const trocaOperacao = (operacao) => {
    estado.operacao = operacao;
  }

  const calcula = () => {
    estado.resultado = 0
    const a = estado.numeroA;
    const b = estado.numeroB;
    let op = estado.operacao;

    switch(op) {
      case 'soma':
        estado.resultado = a + b;
        break;
      case 'subtracao':
        estado.resultado = a - b;
        break;
      case 'multiplicacao':
        estado.resultado = a * b;
        break;
      case 'divisao' :
        if(b != 0) {
          estado.resultado = a / b;
          break;
        } else {
          alert("Impossível dividir por 0, digite outro número.")
        }
    }

    
    
  }
</script>

<template>
  <header class="p-5 mb-4 bg-light rounded-3 text-center">
    <h1>Calculadora Aritmética</h1>
    <h6>Digite dois números e selecione a operação</h6>
  </header>
  <form @submit.prevent="calcula()">
    <div class="row mb-2">
      <div class="col text-center">
        <input @change="e => estado.numeroA = Number(e.target.value)" class="col-md-2" type="number" placeholder="Digite um número">
      </div>
    </div>
    <div class="row mb-2">
      <div class="col text-center">
        <button :class="{selected: estado.operacao === 'soma' }" @click="() => trocaOperacao('soma')" type="button" value="soma" class="btn btn-primary me-2">+</button>
        <button :class="{selected: estado.operacao === 'subtracao' }" @click="() => trocaOperacao('subtracao')" type="button" value="subtracao" class="btn btn-primary me-2">-</button>
        <button :class="{selected: estado.operacao === 'multiplicacao' }" @click="() => trocaOperacao('multiplicacao')" type="button" value="multiplicacao" class="btn btn-primary me-2">*</button>
        <button :class="{selected: estado.operacao === 'divisao' }" @click="() => trocaOperacao('divisao')" type="button" value="divisao" class="btn btn-primary me-2">/</button>
      </div>
    </div>
    <div class="row">
      <div class="col text-center">
        <input @change="e => estado.numeroB = Number(e.target.value)" class="col-md-2" type="number" placeholder="Digite outro número">
      </div>
    </div>
    <div class="row text-center mt-3">
      <div class="col">
        <button type="submit" class="btn btn-primary mb-2">Calcular</button>
      </div>
      <p>Resultado: {{ estado.resultado }}</p>
    </div>
  </form>
</template>

<style scoped>

  .selected {
    background-color: orange;
    border-color: orange;
  }

</style>
