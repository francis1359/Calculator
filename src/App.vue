<script setup>
import { ref } from 'vue'

const inputValue = ref('0')

function pressNumber(numero) {
  const lastOperator = Math.max(
    inputValue.value.lastIndexOf('+'),
    inputValue.value.lastIndexOf('-'),
    inputValue.value.lastIndexOf('*'),
    inputValue.value.lastIndexOf('/'),
  )

  const currentNumber = inputValue.value.slice(lastOperator + 1)

  // No permitir dos puntos en el mismo número
  if (numero === '.' && currentNumber.includes('.')) {
    return
  }

  // Si el primer carácter es un punto, escribir 0.
  if (inputValue.value === '0' && numero === '.') {
    inputValue.value = '0.'
    return
  }

  if (inputValue.value === '0') {
    inputValue.value = numero
  } else {
    inputValue.value += numero
  }
}

function pressOperator(operatorSymbol) {
  const lastCharacter = inputValue.value[inputValue.value.length - 1]

  if (inputValue.value === '0') {
    if (operatorSymbol === '-') {
      inputValue.value = '-'
    }

    return
  }

  if (
    lastCharacter === '+' ||
    lastCharacter === '-' ||
    lastCharacter === '*' ||
    lastCharacter === '/'
  ) {
    return
  }

  inputValue.value += operatorSymbol
}

function calculate() {
  let currentNumber = ''
  const numbers = []
  const operators = []

  for (let i = 0; i < inputValue.value.length; i++) {
    const character = inputValue.value[i]

    if (character === '+' || character === '-' || character === '*' || character === '/') {
      numbers.push(Number(currentNumber))
      operators.push(character)
      currentNumber = ''
    } else {
      currentNumber += character
    }
  }

  if (currentNumber === '') {
    return
  }

  numbers.push(Number(currentNumber))

  console.log(numbers)
  console.log(operators)

  for (let i = 0; i < operators.length; i++) {
    if (operators[i] === '*') {
      numbers[i] = numbers[i] * numbers[i + 1]

      numbers.splice(i + 1, 1)
      operators.splice(i, 1)

      i--
    } else if (operators[i] === '/') {
      numbers[i] = numbers[i] / numbers[i + 1]

      numbers.splice(i + 1, 1)
      operators.splice(i, 1)

      i--
    }
  }

  let result = numbers[0]

  for (let i = 0; i < operators.length; i++) {
    if (operators[i] === '+') {
      result += numbers[i + 1]
    } else if (operators[i] === '-') {
      result -= numbers[i + 1]
    }
  }

  inputValue.value = result.toString()
}

function porcentange() {}

function deleteNumber() {
  inputValue.value = inputValue.value.slice(0, -1)

  if (inputValue.value === '') {
    inputValue.value = '0'
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
      <button class="operator" @click="pressOperator('/')">/</button>
      <button class="number" @click="pressNumber('4')">4</button>
      <button class="number" @click="pressNumber('5')">5</button>
      <button class="number" @click="pressNumber('6')">6</button>
      <button class="operator" @click="pressOperator('*')">x</button>
      <button class="number" @click="pressNumber('1')">1</button>
      <button class="number" @click="pressNumber('2')">2</button>
      <button class="number" @click="pressNumber('3')">3</button>
      <button class="operator" @click="pressOperator('-')">-</button>
      <button class="number" @click="pressNumber('0')">0</button>
      <button class="number" @click="pressNumber('.')">.</button>
      <button class="result" @click="calculate()">=</button>
      <button class="operator" @click="pressOperator('+')">+</button>
      <button class="operator" @click="porcentange('%')">%</button>
      <button class="operator" @click="pressOperator('()')">()</button>
      <button class="clear" @click="clear">Clear</button>
      <button class="delete" @click="deleteNumber()">Delete</button>
    </div>
  </main>
</template>

<style scoped>
main {
  width: 400px;
  margin: 0 auto;
}

.operation {
  width: 100%;
  text-align: right;
  color: gray;
  font-size: 18px;
  margin-bottom: 5px;
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
