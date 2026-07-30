<script setup></script>

<template>
  <main>
    <h1>Calculator</h1>
    <p>My first Vue app</p>

    <input type="text" placeholder="Enter a number" />

    <div class="buttons">
      <button>7</button>
      <button>8</button>
      <button>9</button>
      <button>/</button>
      <button>4</button>
      <button>5</button>
      <button>6</button>
      <button>x</button>
      <button>1</button>
      <button>2</button>
      <button>3</button>
      <button>-</button>
      <button>0</button>
      <button>.</button>
      <button>=</button>
      <button>+</button>
      <button>Clear</button>
      <button>Delete</button>
    </div>
  </main>
</template>

<style scoped>
main {
  width: 400px;
  margin: 0 auto;
}

input {
  width: 100%;
  padding: 10px;
}
.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}
</style>
