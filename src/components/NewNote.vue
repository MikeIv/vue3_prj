<template>


  <div class="new-note">
    <div class="vue-message__wrapper">
      <div class="vue-message">
        <p class="vue-message__txt">Предупреждение об ошибке - <span v-if="message">{{ message }}</span></p>
      </div>
    </div>
    <input v-model="title" type="text" class="new-note__input">
    <textarea v-model="descr"  class="new-note__textarea"></textarea>
    <button class="new-note__btn" @click="addItem">Добавить заметку</button>
  </div>

</template>



<script>

export default {

  data: () => ({
    title: '',
    descr: '',
    message: null
  }),

  methods: {
    addItem () {
      let newitem = {
        title: this.title,
        descr: this.descr,
        date: new Date(Date.now()).toLocaleString(),
      }
      if (this.title === '') {
        this.message = 'Необходимо написать заголовок'
        return false
      }else {
        this.$emit('additem',  newitem)
      }
          this.title = '',
          this.descr = '',
          this.message = null
  }
},



}

</script>