<template>
  <Header :totalExpenses="state.totalExpenses" />
  <Form :state="state" @add-expenses="AddExpenses" />
  <ExpensesList :state="state" @remove-item="removeItem" />
</template>

<script>
import { reactive, computed } from 'vue';
import Header from './components/Header';
import Form from './components/Form';
import ExpensesList from './components/ExpensesList';

export default {
  setup () {
    const state = reactive({
      expenses: [],
      sortedExpenses: computed(() => {
        let temp = [];
        
        temp = state.expenses.sort(function (a, b) {
          return b.date - a.date;
        });

        return temp;
      }),
      totalExpenses: computed(() => {
        let temp = 0;
        if (state.expenses.length > 0) {
          for (let i = 0; i < state.expenses.length; i++) {
            temp += state.expenses[i].value;
          }
          return temp;
        } else {
          return 0;
        }
      })
    });

    function AddExpenses(obj) {
      let d = obj.date.split("-");
      let newD = new Date(d[0], d[1], d[2]);

      state.expenses = [...state.expenses, {
        id: Date.now(),
        desc: obj.desc,
        value: parseInt(obj.value),
        date: newD.getTime()
      }]
    }

    function removeItem(id) {
      state.expenses = state.expenses.filter(v => v.id != id);
    }

    // Return template data
    return {
      Header,
      ExpensesList,
      Form,
      state,
      AddExpenses,
      removeItem
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Fira Sans', sans-serif;
}

body {
  background: yellowgreen;
}
</style>
