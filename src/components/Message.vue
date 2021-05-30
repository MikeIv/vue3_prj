<template>

  <div class="vue-message">
    <p class="vue-message__txt">Предупреждение об ошибке - <span v-if="message">{{ message }}</span></p>
  </div>

</template>



<script>

export default  {
  props: {
    message: {
      type: String,
      required: true
    }
  }
}

</script>

<style lang="scss" scoped>

p {
  color: red;
}

</style>