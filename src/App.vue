<template>
  <div class="app">
    <header>
      <h1>Catatan Penjualan</h1>
    </header>
    <expense-form @add-expense="addExpense"></expense-form>
    <expense-list :expenses="expenses">
      <expense-item-slot></expense-item-slot>
    </expense-list>
    <div class="totals">
      <h2>Jumlah Keseluruhan Penjualan: {{ totalExpense }}</h2>
    </div>
  </div>
</template>

<script>
import ExpenseForm from './components/ExpenseForm.vue';
import ExpenseList from './components/ExpenseList.vue';
import ExpenseItemSlot from './components/ExpenseItemSlot.vue';

export default {
  name: 'App',
  components: {
    ExpenseForm,
    ExpenseList,
    ExpenseItemSlot
  },
  data() {
    return {
      expenses: []
    };
  },
  computed: {
    totalExpense() {
      return this.expenses.reduce((total, expense) => total + expense.total, 0);
    }
  },
  methods: {
    addExpense(expense) {
      this.expenses.push(expense);
    }
  }
}
</script>