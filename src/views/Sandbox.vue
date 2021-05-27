<template>
  <div class="wrapper">

    <div class="wrapper-content">
      <section>
        <div class="container">
          <section class="sandbox">
            <h1 class="v-hidden">Инструменты</h1>

            <article class="sandbox__part">
              <h2 class="sandbox__h2">Vue</h2>

              <h3 class="sandbox__h3">Тестирование компонентов</h3>

              <!-- Message section -->
<!--              <message v-if="message" :message="message" />-->

              <div class="vue-message">
                <p class="vue-message__txt">Предупреждение обшибке - <span v-if="message">{{ message }}</span></p>
              </div>
              <!-- ================ -->


              <!-- newNote section -->
<!--              <newNote :note="note" @plusNote="addNote" />-->

              <div class="new-note">
                <input v-model="note.title" type="text" class="new-note__input">
                <textarea v-model="note.descr"  class="new-note__textarea"></textarea>
                <button @click="addNote" class="new-note__btn">New note</button>

                <h4 class="sandbox__h4 vue-notes__header">Проверка текста - {{ text }}</h4>
              </div>
              <!-- ================ -->


              <!-- VUE App -->
              <div class="vue-notes__header-block">
                <h4 class="sandbox__h4 vue-notes__header">{{ title }}</h4>

<!--                <search />-->


                <!-- Buttons grid control -->
                <section class="vue-notes__h-icon-block">
                  <h3 class="v-hidden">Кнопки визуального отображения блоков</h3>
                  <div class="vue-notes__item-icon" :class="{ active: grid }" @click="grid = true">
                    <svg class="vue-note__icon" role="button">
                      <use xlink:href="#icon-block-view"></use>
                    </svg>
                  </div>
                  <div class="vue-notes__item-icon" :class="{ active: !grid }" @click="grid = false">
                    <svg class="vue-note__icon" role="button">
                      <use xlink:href="#icon-block-view-3"></use>
                    </svg>
                  </div>
                </section>
              </div>

<!--              <notes :notes="notes" :grid="grid" @remove="removeCard" />-->

              <ul class="vue-notes">
                <li class="vue-note" v-for="(note, index) in notes" :key="index" :class="{ notewidth: !grid }">
                  <div class="vue-note__item-icon" @click="removeCard(index)">
                    <svg class="vue-note__icon" aria-hidden="true"
                         role="presentation">
                      <use xlink:href="#icon-close"></use>
                    </svg>
                  </div>
                  <p class="note-header">{{ note.title }}</p>
                  <p class="note-body">{{ note.descr }}</p>
                  <span class="note-datу">{{ note.date }}</span>
                </li>
              </ul>



              <!-- END App -->

              <img alt="Vue logo" src="../assets/img/vue-logo.svg" width="50" height="50">
            </article>
          </section>
        </div>
      </section>
    </div>
  </div>
</template>




<script>

export default {
  name: 'Sandbox',
  components: {

  },
  data: () => ({
    title: 'Блок заметок',
    text: '',
    message: null,

    note: {

      title: '',
      descr: ''
    },


    notes: [
      {
        title: 'Заметка №1',
        descr: 'Содержание заметки',
        date: new Date(Date.now()).toLocaleString()
      },
      {
        title: 'Заметка №2',
        descr: 'Содержание заметки',
        date: new Date(Date.now()).toLocaleString()
      },
      {
        title: 'Заметка №3',
        descr: 'Содержание заметки',
        date: new Date(Date.now()).toLocaleString()
      }
    ]
  }),
  methods: {
    addNote () {
      let {title, descr} = this.note

      if(title === '') {
        this.message = 'Заполните поля!'
        return false
      }

      this.notes.push({
        title,
        descr,
        date: new Date(Date.now()).toLocaleString()
      })
    }
  }

}
</script>



<style lang="scss">

.page__body {
  display: grid;
  grid-template-areas:
    "header"
    "main"
    "footer";
  grid-template-rows: 12.8rem 1fr 0;
  grid-template-columns: 1fr;

  // min-height: 100vh;

  margin: 0;
  padding: 0;

  box-sizing: border-box;
}

.header-section {
  display: block;
}

</style>