<template>
  <h2>My transactions</h2>
  <ul>
    <transactions-item
      v-for="transaction in transactions"
      :key="transaction.id"
      :type="transaction.type"
      :id="transaction.id"
      :category="transaction.category"
      :account="transaction.account"
      :description="transaction.description"
      :amount="transaction.amount"
      :date="transaction.date"
    ></transactions-item>
  </ul>
</template>

<script>
import TransactionsItem from "./TransactionsItem";
export default {
  components: {
    TransactionsItem,
  },
  inject: ["transactions"],
};
</script>

<style scoped>
ul {
  margin: 0 0 2rem;
  padding: 0;
  list-style: none;
}
</style>