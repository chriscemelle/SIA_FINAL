<template>
  <header>
    <h1>Expenses Tracker</h1>
    <div class="total-expenses">PHP{{ totalExpenses }}</div>
  </header>
</template>

<script>
export default {
  props: {
    totalExpenses: Number
  }
}
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 30px;
  background-color: teal;
  border-bottom: 5px solid green;
}

header h1 {
  color: paleturquoise;
  font-size: 28px;
}

header .total-expenses {
  font-family: 'Fira Code', 'Fira Sans', sans-serif;
  background-color: #9900ff;
  color: paleturquoise;
  font-size: 20px;
  font-weight: 900;
  padding: 5px 10px;
  min-width: 100px;
  text-align: center;
  border-radius: 8px;
  box-shadow: inset 0px 0px 6px rgba(0, 0, 0, 0.25);
  text-shadow: 0px 3px 3px rgba(0, 0, 0, 0.25);
}
</style>