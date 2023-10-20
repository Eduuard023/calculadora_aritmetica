<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';
import Resultado from './components/Resultado.vue';

const estado = reactive({
  filtro: 'soma',
  num1: '',
  num2: '',
  resultado: '',
})

const soma = () =>{
  const resultadoSoma = estado.num1 + estado.num2;
  estado.resultado = resultadoSoma;
  return estado.resultado
}

const subtracao = () =>{
  const resultadoSubtracao = estado.num1 - estado.num2;
  estado.resultado = resultadoSubtracao;
  return estado.resultado
}

const multiplicacao = () =>{
  const resultadoMultiplicacao = estado.num1 * estado.num2;
  estado.resultado = resultadoMultiplicacao;
  return estado.resultado
}

const divisao = () =>{
  const resultadoDivisao = estado.num1 / estado.num2;
  estado.resultado = resultadoDivisao;
  return estado.resultado
}


</script>

<template>
  <div class="container">
    <div class="background-color">
      <Cabecalho />
      <Formulario :primeiro-input=" evento => estado.num1 = evento.target.value" :segundo-input="evento => estado.num2 = evento.target.value" :filtro="estado.filtro" :selecionaFiltro="evento => estado.filtro = evento.target.value" />
      <Resultado :filtro="estado.filtro" :funcaoSoma="soma()" :funcaoSub="subtracao()" :funcaoMult="multiplicacao()" :funcaoDivisao="divisao()" />
    </div>
  </div>
</template>

<style scoped>
  .container {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;

  width: 200vw;
  height: 100vh;

  padding: 0;
  padding-bottom: 196px;
}

.background-color {
  border: 1px solid #000;
  border-radius: 10px;
  padding: 56px;
  background-color: #ccc;
}

@media screen and (min-width: 360px) {
  .container {
    width: 80%;
  }
}
</style>
