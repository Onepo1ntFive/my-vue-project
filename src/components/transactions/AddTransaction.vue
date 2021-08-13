<template>
  <h2>Add transaction</h2>
  <form @submit.prevent="submitForm">
    <div>
      <label for="category">Категория</label>
      <select name="category" id="category" ref="inputCategory">
        <option value="null" selected disabled hidden>Категория</option>
        <option value="Продукты">Продукты</option>
        <option value="Зарплата">Зарплата</option>
        <option value="Вкусняшки">Вкусняшки</option>
        <option value="Машина">Машина</option>
        <option value="Бензин">Бензин</option>
        <option value="Дом">Дом</option>
        <option value="Бытовая химия">Бытовая химия</option>
        <option value="Жизнь и здоровье">Жизнь и здоровье</option>
      </select>
    </div>
    <div>
      <label for="account">Счет</label>
      <select name="account" id="account" ref="inputAccount">
        <option value="null" selected disabled hidden>Счет</option>
        <option value="Tinkoff">Tinkoff</option>
        <option value="Сбербанк">Сбербанк</option>
        <option value="Наличные">Наличные</option>
      </select>
    </div>
    <div>
      <label for="date">Дата</label>
      <input id="date" type="date" ref="inputDate" :value="dateToday" />
    </div>
    <div>
      <label for="description">Описание</label>
      <input id="description" type="text" autocomplete="off" ref="inputDesc" />
    </div>
    <div class="form-w100">
      <span class="radio">
        <input
          type="radio"
          name="type"
          id="income"
          ref="inputTypeIncome"
          checked
        />
        <label for="income">Расход</label>
      </span>
      <span class="radio">
        <input type="radio" name="type" id="expense" ref="inputTypeExpense" />
        <label for="expense">Доход</label>
      </span>
    </div>
    <div>
      <label for="amount">Количество</label>
      <input id="amount" type="text" autocomplete="off" value="0" ref="inputAmount" />
    </div>
    <div class="form-w100">
      <base-button type="submit">Добавить</base-button>
    </div>
  </form>
</template>

<script>
export default {
  inject: ['addTransaction'],
  methods: {
    submitForm() {
      const enteredCategory = this.$refs.inputCategory.value;
      const enteredAccount = this.$refs.inputAccount.value;
      const enteredDate = this.$refs.inputDate.value;
      const enteredDesc = this.$refs.inputDesc.value;
      const enteredType = this.$refs.inputTypeIncome.checked
        ? "expense"
        : "income";
      const enteredAmount = this.$refs.inputAmount.value;

      console.log(enteredCategory, enteredAccount)

      this.addTransaction(enteredCategory, enteredAccount, enteredDate, enteredDesc, enteredType, enteredAmount);
    },
  },
  computed: {
    dateToday() {
      return new Date().toISOString().slice(0, 10);
    },
  },
};
</script>

<style scoped>
label {
  padding-bottom: 0.5rem;
  display: block;
  width: 100%;
  font-size: 0.9rem;
  color: gray;
  cursor: pointer;
}
form {
  margin-left: -1rem;
  margin-right: -1rem;
  display: flex;
  flex-flow: row wrap;
}
div {
  padding-left: 1rem;
  padding-right: 1rem;
  width: 50%;
  display: flex;
  flex-flow: row wrap;
  margin-bottom: 1rem;
}
div.form-w100 {
  width: 100%;
}
input:not([type="radio"]),
select,
textarea {
  border: 1px solid gray;
  height: 2rem;
  width: 100%;
}
textarea {
  height: 50px;
  resize: none;
}
.radio {
  margin-right: 1rem;
  width: auto;
  display: flex;
  flex-flow: row wrap;
  align-items: center;
}
.radio label {
  margin: 0;
  padding: 0;
  display: inline-block;
  width: auto;
}
.radio input {
  margin: 0;
  padding: 0;
  margin-right: 0.5rem;
  display: inline-block;
  width: auto;
}
</style>