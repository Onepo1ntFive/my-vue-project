<template>
  <li>
    <header>
      <p class="categoty">{{ category }}</p>
      <p class="account">{{ account }}</p>
      <p class="description">{{ description }}</p>
      <p class="date">{{ date }}</p>
      <nav><base-button mode="flat" @click="removeTransaction">&times;</base-button></nav>
    </header>
    <div class="amount" :class="typeClass">{{ resultAmount }}</div>
  </li>
</template>

<script>
export default {
  props: ["type", "id", "category", "account", "description", "amount", "date"],
  computed: {
    resultAmount() {
      const symbol = this.type === "expense" ? "-" : "+";
      return `${symbol}${this.amount} ₽`;
    },
    typeClass() {
      return this.type === "expense" ? "expense" : "income";
    },
  },
  inject: ["removeTransaction"],
};
</script>

<style scoped>
li {
  position: relative;
  padding: 1rem 0;
  display: flex;
  flex-flow: row nowrap;
  align-items: flex-end;
  justify-content: space-between;
  border-bottom: 1px solid lightgray;
}
p {
  margin: 0;
  margin-bottom: 0.2rem;
}
.description {
  font-size: 0.8rem;
  color: gray;
}
.date {
  font-size: 0.9rem;
  color: gray;
}
.income {
  color: lightgreen;
}
.expense {
  color: tomato;
}
li button {
  padding: 0 0.5rem 0.2rem;
  position: absolute;
  right: 0;
  top: 1rem;
  font-size: 1.5rem;
  font-weight: 300;
}
</style>