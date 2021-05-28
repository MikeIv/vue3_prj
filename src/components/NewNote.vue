<template>


  <div class="new-note">
    <input v-model="title" type="text" class="new-note__input">
    <textarea v-model="descr"  class="new-note__textarea"></textarea>
    <button @click="$emit(addNote)" class="new-note__btn">Добавить заметку</button>

    <h4 class="sandbox__h4 vue-notes__header">Проверка текста - {{ text }}</h4>
  </div>

</template>



<script>
export default  {
  props: {
    note: {
      type: Object,
      required: true
    }
  },
  methods: {
    addNote () {
      this.note
    }
  }
}

</script>