<script setup>
import { reactive } from 'vue';

const estado = reactive ({
  primeiroNumero: 0,
  segundoNumero: 0,
  filtro: 'somar',
})
function Somar(){
  const { primeiroNumero, segundoNumero } = estado;
  return parseInt(primeiroNumero) + parseInt(segundoNumero);
}
function Diminuir(){
  const { primeiroNumero, segundoNumero } = estado;
  return parseInt(primeiroNumero) - parseInt(segundoNumero);
}
function Multiplicar(){
  const { primeiroNumero, segundoNumero } = estado;
  return parseInt(primeiroNumero) * parseInt(segundoNumero);
}
function Dividir(){
  const { primeiroNumero, segundoNumero } = estado;
  return parseInt(primeiroNumero) / parseInt(segundoNumero);
}

const getOperacao = () => {
  const { filtro } = estado;

  switch (filtro) {

    case 'somar':
      return Somar();
    
      case 'diminuir':
      return Diminuir();
    
    case 'multiplicar':
      return Multiplicar();

    case 'dividir':
      return Dividir();  

    Default:
      return Somar();
  }
}
</script>
<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light rounded-3 ">
      <h1>Calculadora Aritmetica</h1>
      <p>Escolha um das 4 operações</p>
    </header>
    <form>
      <div class="row">
        <div class="col">
          <input @keyup="evento => estado.primeiroNumero = evento.target.value" type="number" placeholder="primeiro numero" class="form-control mr-3a">
          <input @keyup="evento => estado.segundoNumero = evento.target.value" type="number" placeholder="segundo numero" class="form-control">
        </div>
        <div class="col-md-4">
          <select @change="evento => estado.filtro = evento.target.value" class="form-control">
            <option value="somar">+</option>
            <option value="diminuir">-</option>
            <option value="multiplicar">x</option>
            <option value="dividir">:</option>
          </select>
        </div>
      </div>
      Resultado: {{ getOperacao() }}
    </form>
    
  </div>
</template>

<style scoped>
</style>
