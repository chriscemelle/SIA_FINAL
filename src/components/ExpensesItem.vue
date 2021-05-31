<template>
  <div class="expenses-item">
    <div class="removeItem" @click="removeItem">x</div>
    <div class="desc">
      {{ expenses.desc }}
    </div>
    <div class="price">
      PHP{{ expenses.value }}
    </div>
    <div class="date">
      {{ formattedDate }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    expenses: Object
  },
  setup (props, { emit }) {
    
    let date = new Date(props.expenses.date);
    let day = date.getDate();
    let month = date.getMonth();
    let year = date.getFullYear();

    let formattedDate = day + "/" + month + "/" + year;

    function removeItem () {
      emit("remove-item", props.expenses.id);
    }

    return {
      formattedDate,
      removeItem
    }
  }
}
</script>

<style scoped>
  .expenses-item {
    position: relative;
    display: flex;
    padding: 15px 15px 15px 0px;
    background-color: #FFF;
    border-radius: 8px;
    max-width: 600px;
    margin: 0 auto 30px;
  }

  .removeItem {
    color: #EF2D2D;
    font-weight: 600;
    font-size: 20px;
    line-height: 1;
    text-align: center;
    margin: 0 15px;
  }

  .desc {
    color: #666;
    flex: 1 1 100%;
    font-size: 20px;
  }

  .price {
    color: #666;
    min-width: 100px;
    font-size: 20px;
  }

  .date {
    color: #666;
    text-align: right;
    font-size: 20px;
  }
</style>