<template>
  <div>
    <h2>Riwayat Pembelanjaan</h2>
    <slot name="expense" v-for="(expense, index) in expenses" :key="index" :expense="expense">
      <div>
        {{ expense.description }} - {{ expense.price }} - {{ expense.quantity }} - Total: {{ expense.total }}
      </div>
    </slot>
    <div v-if="expenses.length === 0">Belum ada pembelanjaan.</div>
    <div>Total Pengeluaran: {{ totalExpense }}</div>
  </div>
</template>

<script>
export default {
  name: 'ExpenseList',
  props: {
    expenses: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      totalExpense: 0
    };
  },
  watch: {
    expenses: {
      handler(newVal) {
        this.calculateTotalExpense(newVal);
      },
      deep: true
    }
  },
  methods: {
    calculateTotalExpense(expenses) {
      this.totalExpense = expenses.reduce((total, expense) => total + expense.total, 0);
    }
  }
}
</script>
