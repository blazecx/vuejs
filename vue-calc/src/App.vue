<template>
  <div class="calculator">
    <h1>Простой калькулятор</h1>
    <div class="input-group">
      <input type="number" v-model.number="num1">
    </div>
    <div class="input-group">
      <select v-model="operator">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
    </div>
    <div class="input-group">
      <input type="number" v-model.number="num2">
    </div>
    <p class="result">= {{ calculate() }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num1: 0,
      num2: 0,
      operator: '+'
    }
  },
  methods: {
    calculate() {
      switch (this.operator) {
        case '+':
          return this.num1 + this.num2;
        case '-':
          return this.num1 - this.num2;
        case '*':
          return this.num1 * this.num2;
        case '/':
          if (this.num2 !== 0) {
            return this.num1 / this.num2;
          } else {
            return 'Ошибка: Деление на ноль';
          }
        default:
          return 'Ошибка: Неизвестный оператор';
      }
    }
  }
}
</script>

<style scoped>
.calculator {
  width: 300px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f5f5f5;
  border-radius: 5px;
}

.input-group {
  margin-bottom: 10px;
}

.result {
  font-size: 24px;
  font-weight: bold;
  color: #333;
}
</style>