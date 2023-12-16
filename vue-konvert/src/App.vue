<template>
  <div>
    <h1>Конвертер валют</h1>
    <div>
      <label for="amount">Сумма:</label>
      <input type="number" id="amount" v-model.number="amount">
    </div>
    <div>
      <label for="from">Из:</label>
      <select id="from" v-model="fromCurrency">
        <option v-for="currency in currencies" :key="currency" :value="currency">{{ currency }}</option>
      </select>
    </div>
    <div>
      <label for="to">В:</label>
      <select id="to" v-model="toCurrency">
        <option v-for="currency in currencies" :key="currency" :value="currency">{{ currency }}</option>
      </select>
    </div>
    <p>{{ convert() }}</p>
  </div>
</template>

<script
>
export default {
  data() {
    return {
      amount: 0,
      fromCurrency: 'USD',
      toCurrency: 'EUR',
      currencies: ['USD', 'EUR', 'GBP', 'RUB'],
      rates: {
        'USD': 1,
        'EUR': 0.85,
        'GBP': 0.75,
        'RUB': 89.67
      }
    }
  },
  methods: {
    convert() {
      if (this.amount === 0) {
        return 'Введите сумму'
      }
      const fromRate = this.rates[this.fromCurrency]
      const toRate = this.rates[this.toCurrency]
      return `${this.amount} ${this.fromCurrency} = ${(this.amount / fromRate * toRate).toFixed(2)} ${this.toCurrency}`
    }
  }
}
</script>