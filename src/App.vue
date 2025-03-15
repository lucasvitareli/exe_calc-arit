<script setup>
import { reactive } from 'vue';

const state = reactive ({
  answer: 0,
  value1: 0,
  value2: 0,
  operation: 'sum'
})

function getNumber1(event) {
  state.value1 = event.target.value;
  if (state.value1 === '') {
    state.value1 = 0;
  }
  calculate();
}

function getNumber2(event) {
  state.value2 = event.target.value;
  if (state.value2 === '') {
    state.value2 = 0;
  }
  calculate();
}

function getOperation(event) {
  state.operation = event.target.value;
  calculate();
}

function calculate() {
  const num1 = Number(state.value1);
  const num2 = Number(state.value2);

  switch (state.operation) {
    case 'sum' :
      state.answer = num1 + num2;
      break;
    case 'sub' :
      state.answer = num1 - num2;
      break;
    case 'mul' :
      state.answer = num1 * num2;
      break;
    case 'div' :
      state.answer = num2 !== 0 ? num1 / num2 :
      alert('Não é possível dividir por zero');
      break;
  }
}


</script>

<template>
    <div class="container">
      <div class="calculator">
        <h1>Calculadora Aritmética</h1>
        <div class="result">
          <p>
            <span id="answer"> {{ state.answer }} </span>
          </p>
        </div>
        <div class="values">
          <input type="number" id="value1" placeholder="0" required v-model="state.value1" @input="calculate">  <!-- @input serve para atualizar o valor do input -->
          <select id="operation" v-model="state.operation" @change="calculate"> 
            <option value="sum">+</option>
            <option value="sub">-</option>
            <option value="mul">*</option>
            <option value="div">/</option>
          </select>
          <input type="number" id="value2" placeholder="0" required v-model="state.value2" @input="calculate">
        </div>
      </div>
    </div>
</template>

<style scoped>
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }

  .calculator {
    background-color: coral;
    padding: 26px;
    border-radius: 22px;
  }

  h1 {
    text-align: center;
  }

  .result {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 auto;
    width: 30%;
    background-color: #fff;
    margin-bottom: 22px;
    border: 1px solid #000;
    border-radius: 12px;
  }

  input[type="number"] {
    width: 100px;
    padding: 10px;
    border-radius: 12px;
    border: 1px solid #000;
    text-align: center;
  }

  select {
    padding: 10px;
    border-radius: 12px;
    border: 1px solid #000;
    margin: 0 12px 0 12px;
  }
    
  
</style>
