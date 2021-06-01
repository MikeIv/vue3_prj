<template>
  <div class="vue_search_wrapper">

    <div class="vue_search">
      <input class="vue_search__input" type="text" v-model="search" :placeholder="placeholder">
    </div>

  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      required: true
    },
    placeholder: {
      type: String,
      default: 'Поиск'
    }
  },
  data() {
    return {search: this.value}
  },
  watch: {
    search(val) {
      this.$emit('search', val)
      console.log(val)
    }
  }
}
</script>

<style scoped>

</style>