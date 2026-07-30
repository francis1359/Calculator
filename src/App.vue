<script setup></script>

<template>
  <main>
    <h1>Calculator</h1>

    <input type="text" placeholder="Enter a number" />

    <div class="buttons">
      <button class="number">7</button>
      <button class="number">8</button>
      <button class="number">9</button>
      <button class="operator">/</button>
      <button class="number">4</button>
      <button class="number">5</button>
      <button class="number">6</button>
      <button class="operator">x</button>
      <button class="number">1</button>
      <button class="number">2</button>
      <button class="number">3</button>
      <button class="operator">-</button>
      <button class="number">0</button>
      <button class="number">.</button>
      <button class="result">=</button>
      <button class="operator">+</button>
      <button class="operator">%</button>
      <button class="operator">()</button>
      <button class="clear">Clear</button>
      <button class="delete">Delete</button>
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
