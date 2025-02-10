<script setup>
  import { reactive } from 'vue';


  const estado = reactive({
    numeroA: 0,
    numeroB: 0,
    operacao: 'soma',
    resultado: 0
  })

  const trocaOperacao = (e) => {
    estado.operacao = e.target.value;
    console.log(estado.operacao);
  }

  const calcula = () => {
    estado.resultado = 0
    const a = estado.numeroA;
    const b = estado.numeroB;
    let op = estado.operacao;

    switch(op) {
      case 'soma':
        return estado.resultado = a + b;
      case 'subtracao':
        return estado.resultado = a - b;
      case 'multiplicacao':
        return estado.resultado = a * b;
      case 'divisao' :
        if(b != 0) {
          return estado.resultado = a / b;
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
        <input @keyup="e => estado.numeroA = Number(e.target.value)" class="col-md-2" type="number" placeholder="Digite um número">
      </div>
    </div>
    <div class="row mb-2">
      <div class="col-md-2 mx-auto">
        <select class="form-control" @change="trocaOperacao">
          <option value="soma">Soma</option>
          <option value="subtracao">Subtração</option>
          <option value="multiplicacao">Multiplicação</option>
          <option value="divisao">Divisão</option>
        </select>
      </div>
    </div>
    <div class="row">
      <div class="col text-center">
        <input @keyup="e => estado.numeroB = Number(e.target.value)" class="col-md-2" type="number" placeholder="Digite outro número">
      </div>
    </div>
    <div class="row text-center mt-3">
      <p>Resultado: {{ calcula() }}</p>
    </div>
  </form>
</template>

<style scoped>

  .selected {
    background-color: orange;
    border-color: orange;
    
  }

  .selected:hover {
    background-color: orange;
    border-color: orange;
    
  }

</style>
