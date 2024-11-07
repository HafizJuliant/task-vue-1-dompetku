<template>
  <div class="container">
    <h2 class="title">Dompetku – Expense & Income Management</h2>
    <div class="input-form">
      <input v-model="description" type="text" placeholder="Description" class="input-field" />
      <input v-model.number="amount" type="number" placeholder="Amount" class="input-field" />
      <button @click="addTransaction" class="submit-btn">Add Transaction</button>
    </div>
    <ul class="transaction-list">
      <li v-for="(transaction, index) in transactions" :key="index" class="transaction-item">
        <span>{{ transaction.description }} - ${{ transaction.amount.toFixed(2) }}</span>
        <button @click="removeTransaction(index)" class="delete-btn">Delete</button>
      </li>
    </ul>
    <button @click="clearAll" class="clear-all-btn">Clear All</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      description: '',
      amount: null,
      transactions: [],
    }
  },
  methods: {
    addTransaction() {
      if (this.description && this.amount) {
        this.transactions.push({
          description: this.description,
          amount: this.amount,
        })
        this.description = ''
        this.amount = null
      }
    },
    removeTransaction(index) {
      this.transactions.splice(index, 1)
    },
    clearAll() {
      this.transactions = []
    },
  },
}
</script>

<style scoped>
/* Main Container */
.container {
  width: 90vw;
  height: 80vh;
  margin: auto;
  text-align: center;
  font-family: 'Roboto', sans-serif;
  background-color: #ffffff;
  border-radius: 12px;
  padding: 3em;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
  font-size: 1.2em;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  color: #333;
  transition: all 0.3s ease;
}

/* Title */
.title {
  color: #2c3e50;
  font-size: 2.8em;
  margin-bottom: 1.5em;
  font-weight: bold;
  letter-spacing: 1px;
}

/* Input Form */
.input-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 2em;
  gap: 1em;
}

/* Styling untuk input field */
.input-field {
  width: 60%;
  padding: 0.8em;
  margin: 0.5em;
  border-radius: 8px;
  border: 2px solid #ccc;
  font-size: 1.1em;
  transition: all 0.3s ease;
}

.input-field:focus {
  border-color: #1abc9c;
  outline: none;
}

.input-field::placeholder {
  color: #aaa;
  font-style: italic;
}

/* Submit Button */
.submit-btn {
  padding: 0.8em 2em;
  background-color: #3498db;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 1.2em;
  cursor: pointer;
  transition:
    background-color 0.3s ease,
    transform 0.3s ease;
}

.submit-btn:hover {
  background-color: #2980b9;
  transform: scale(1.05);
}

/* Transaction List */
.transaction-list {
  list-style: none;
  padding: 0;
  margin: 0;
  width: 100%;
}

.transaction-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 1em 0;
  padding: 1.2em;
  background-color: #f9fafb;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  font-size: 1.1em;
  transition: all 0.3s ease;
}

.transaction-item:hover {
  transform: translateY(-5px);
}

.transaction-item span {
  color: #34495e;
}

.delete-btn {
  background-color: #e74c3c;
  color: white;
  padding: 0.6em 1.2em;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 1.1em;
  transition:
    background-color 0.3s ease,
    transform 0.3s ease;
}

.delete-btn:hover {
  background-color: #c0392b;
  transform: scale(1.05);
}

/* Clear All Button */
.clear-all-btn {
  margin-top: 2em;
  background-color: #f39c12;
  color: white;
  padding: 0.8em 2em;
  border: none;
  border-radius: 8px;
  font-size: 1.2em;
  cursor: pointer;
  transition:
    background-color 0.3s ease,
    transform 0.3s ease;
}

.clear-all-btn:hover {
  background-color: #e67e22;
  transform: scale(1.05);
}
</style>
