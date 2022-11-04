<template>
  <div>
    <div class="display">
      <input v-model="operand1"/>
      <input v-model="operand2"/>
      = {{result}}
    </div>
    <div class="keyboard">
      <button v-on:click="result = Number(operand1) + Number(operand2)">+</button>
      <button v-on:click="result = operand1 - operand2">-</button>
      <button v-on:click="result = operand1 * operand2">*</button>
      <button v-on:click="result = operand1 / operand2">/</button>
      <button v-on:click="result = Math.pow(operand1, operand2)">**</button>
      <button v-on:click="result = Math.floor(operand1 / operand2)">%</button>

    </div>
  </div>
</template>

<script>
export default {
  name: 'Calculate-1',
  data() {
    return {
      operand1: "",
      operand2: "",
      result: ""
    }
  }
}
</script>

<style scoped>
input {
  color: green;
  border: 2px solid green;
  padding: 10px;
  font-size: large;

}
button {
  padding: 10px;
  color: red;
  margin: 15px;
}
</style>
