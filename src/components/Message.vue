<template>
  <div class="vue-message">
    <p>Сообщение - {{ message }}</p>
  </div>

</template>

<script>


export default  {
  props: {
    data: {
      message: 'Проверка записи'
    }
  }
}


</script>

<style lang="scss" scoped>

p {
  color: red;
}

</style>