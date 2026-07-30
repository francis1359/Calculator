<script setup>
import { ref } from 'vue'

const inputValue = ref('0')

function pressNumber(numero) {
  if (inputValue.value === '0') {
    inputValue.value = numero
  } else {
    inputValue.value = inputValue.value + numero
  }
}

function clear() {
  inputValue.value = '0'
}
</script>

<template>
  <main>
    <h1>Calculator</h1>

    <input type="text" :value="inputValue" placeholder="Enter a number" />

    <div class="buttons">
      <button class="number" @click="pressNumber('7')">7</button>
      <button class="number" @click="pressNumber('8')">8</button>
      <button class="number" @click="pressNumber('9')">9</button>
      <button class="operator" @click="pressNumber('/')">/</button>
      <button class="number" @click="pressNumber('4')">4</button>
      <button class="number" @click="pressNumber('5')">5</button>
      <button class="number" @click="pressNumber('6')">6</button>
      <button class="operator" @click="pressNumber('*')">x</button>
      <button class="number" @click="pressNumber('1')">1</button>
      <button class="number" @click="pressNumber('2')">2</button>
      <button class="number" @click="pressNumber('3')">3</button>
      <button class="operator" @click="pressNumber('-')">-</button>
      <button class="number" @click="pressNumber('0')">0</button>
      <button class="number" @click="pressNumber('.')">.</button>
      <button class="result" @click="pressNumber('=')">=</button>
      <button class="operator" @click="pressNumber('+')">+</button>
      <button class="operator" @click="pressNumber('%')">%</button>
      <button class="operator" @click="pressNumber('()')">()</button>
      <button class="clear" @click="clear('C')">Clear</button>
      <button class="delete" @click="pressNumber('DEL')">Delete</button>
    </div>
  </main>
</template>

<style scoped>
main {
  width: 400px;
  margin: 0 auto;
}

input {
  width: 90%;
  padding: 20px 18px;
  margin-bottom: 10px;
  border-radius: 5px;
  text-align: right;
  font-size: 1.5rem;
}
.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

button {
  height: 50px;
  border-radius: 5px;
  border: none;
}

.number {
  background-color: #f0f0f0;
}

.operator {
  background-color: #f9a825;
  color: white;
}

.result {
  background-color: #43a047;
  color: white;
}

.clear {
  background-color: #e53935;
  color: white;
}

.delete {
  background-color: #757575;
  color: white;
}
</style>
