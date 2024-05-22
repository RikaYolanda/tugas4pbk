<template>
  <div>
    <h2 bg color="brown">Shoes Yolanda</h2>
    <form @submit.prevent="submitForm" class="expense-form">
      <div class="form-group">
        <label for="description">Jenis Sepatu</label>
        <input type="text" v-model="description" class="form-control" placeholder="Masukkan nama sepatu">
      </div>
      <div class="form-group">
        <label for="price">Harga Sepatu</label>
        <input type="number" v-model.number="price" class="form-control" placeholder="Masukkan harga sepatu">
      </div>
      <div class="form-group">
        <label for="quantity">Jumlah Sepatu</label>
        <input type="number" v-model.number="quantity" class="form-control" placeholder="Masukkan jumlah sepatu">
      </div>
      <button type="submit" class="btn">Tambah Pembelanjaan</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'ExpenseForm',
  data() {
    return {
      description: '',
      price: '',
      quantity: ''
    };
  },
  methods: {
    submitForm() {
      const total = this.price * this.quantity;
      const expense = {
        description: this.description,
        price: this.price,
        quantity: this.quantity,
        total: total
      };
      this.$emit('add-expense', expense);
      this.clearForm();
    },
    clearForm() {
      this.description = '';
      this.price = 0;
      this.quantity = 1;
    }
  }
}
</script>

<style scoped>
.expense-form {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.form-group {
  display: flex;
  flex-direction: column;
}

label {
  margin-bottom: 5px;
}

.form-control {
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 3px;
}

.btn {
  background-color: #db34db;
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
}

.btn:hover {
  background-color: #9321aa;
}
</style>
