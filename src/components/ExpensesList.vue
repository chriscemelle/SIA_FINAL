<template>
  <div class="expenses-list">
    <ExpensesItem v-for="obj in state.sortedExpenses" :key="obj.id" :expenses="obj" @remove-item="removeItem" />
  </div>
</template>

<script>
import ExpensesItem from './ExpensesItem';

export default {
  props: {
    state: Object
  },
  setup (props, { emit }) {
    function removeItem(id) {
      emit( 'remove-item', id );
    }

    return {
      ExpensesItem,
      removeItem
    }
  }
}
</script>

<style scoped>
  .expenses-list {
    margin-top: 30px;
    padding: 15px;
  }
</style>