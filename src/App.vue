<template>
  <the-header>
    <h1>hutwood wallet app</h1>
  </the-header>
  <transactions-list v-if="storedTransactions.length"></transactions-list>
  <add-transaction></add-transaction>
</template>

<script>
import TheHeader from "./components/layouts/TheHeader";
import TransactionsList from "./components/transactions/TransactionsList";
import AddTransaction from "./components/transactions/AddTransaction";

export default {
  components: {
    TheHeader,
    TransactionsList,
    AddTransaction,
  },
  data() {
    return {
      storedTransactions: [
        {
          id: "transaction-1",
          type: "expense",
          category: "Продукты",
          account: "Tinkoff",
          description: "На неделю в пятерочке",
          amount: 115.5,
          date: "12.08.2021",
        },
        {
          id: "transaction-2",
          type: "income",
          category: "Зарплата",
          account: "Tinkoff",
          description: "",
          amount: 1000000,
          date: "01.08.2021",
        },
        {
          id: "transaction-1",
          type: "expense",
          category: "Вкусняшки",
          account: "Tinkoff",
          description: "Немного сладости для жирной жопки",
          amount: 1252.02,
          date: "20.07.2021",
        },
      ],
    };
  },
  provide() {
    return {
      transactions: this.storedTransactions,
      removeTransaction: this.removeItem,
      addTransaction: this.addItem,
    };
  },
  methods: {
    addItem(category, account, date, desc, type, amount) {
      const newTransaction = {
        id: new Date().toISOString(),
        type: type,
        category: category,
        account: account,
        description: desc,
        amount: amount,
        date: date,
      };
      this.storedTransactions.unshift(newTransaction);
    },
    removeItem(itemId) {
      const itemIndex = this.storedTransactions.findIndex(
        (item) => item.id === itemId
      );
      this.storedTransactions.splice(itemIndex, 1);
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700;900&display=swap");
* {
  box-sizing: border-box;
}
html {
  font-family: "Roboto", sans-serif;
  font-size: 1rem;
}
body {
  margin: 0;
  padding: 1rem;
}
h1,
h2,
h3 {
  font-weight: 300;
}
input,
textarea,
select {
  font-family: "Roboto", sans-serif;
}
#app {
  margin: auto;
  max-width: 50rem;
}
</style>
