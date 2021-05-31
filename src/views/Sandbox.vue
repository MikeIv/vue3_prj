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
              <!-- ================ -->

              <!-- newNote section -->
              <newNote @additem="addItem"  />
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

              <!-- Notes section -->
              <notes :items="items" @remove="removeItem"  />
              <!-- ================ -->

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

import notes from '@/components/Notes.vue'
import newNote from '@/components/NewNote.vue'

export default {
  name: 'Sandbox',
  components: {
    newNote,
    notes

  },
  data: () => ({
    title: 'Раздел заметок',
    text: '',
    grid: true,

    note: {
      title: '',
      descr: ''
    },

    items: [
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
    ],

  }),
  methods: {
    addItem (item) {
        this.items.push(item)
      },
      removeItem (index) {
        this.items.splice(index, 1)
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