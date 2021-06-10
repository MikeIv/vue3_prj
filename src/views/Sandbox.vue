<template>
  <div class="wrapper">

    <div class="wrapper-content">

        <div class="container">
          <section class="sandbox">
            <h1 class="v-hidden">Инструменты</h1>

            <article class="sandbox__part">
              <h2 class="sandbox__h2">Vue</h2>

              <h3 class="sandbox__h3">Тестирование компонентов</h3>

              <!-- newNote section -->
              <newNote @additem="addItem"  />
              <!-- ================ -->

              <!-- Header section -->
              <div class="vue-notes__header-block">
                <h4 class="sandbox__h4 vue-notes__header">{{ title }}</h4>
                <search
                    :value="search"
                    @search="search = $event"
                    placeholder="Поиск"  />


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
              <!-- ================ -->

              <!-- Notes section -->
              <notes :items="itemsFilter" @remove="removeItem" :grid="grid" />
              <!-- ================ -->


              <!-- MODALS -->
              <div class="modal__section-wrapper">
                <!-- first modal -->
                <div class="modal__btn-wrapper">
                  <button class="modal__btn" @click="modalView = !modalView">Открыть</button>
                </div>

                <modals v-show="modalView" @close="modalView = false">
                  <slot class="modal__info-block">
                    <p class="modal__info-txt">Содержимое окна</p>
                  </slot>
                </modals>

                <!-- second modal -->
                <div class="modal__btn-wrapper">
                  <button class="modal__btn" @click="modalForm.show = !modalForm.show">Открыть форму</button>
                </div>

                <modals v-show="modalForm.show" @close="modalForm.show = false" title="Modal with Form">
                  <slot>
                    <form class="modal__form" @submit.prevent="submitForm">
                      <label class="modal__label">Имя:</label>
                      <input type="text" class="modal__input" v-model="modalForm.name" required>
                      <label class="modal__label">Email:</label>
                      <input type="email" class="modal__input" v-model="modalForm.email" required>
                      <button class="modal__btn modal__btn--submit">Отправить</button>
                    </form>
                  </slot>
                </modals>


                <!-- modal validate -->
                <div class="modal__btn-wrapper">
                  <button class="modal__btn" @click="modalValidate = !modalValidate">Форма с валидацией</button>
                </div>
                <modalValidate v-show="modalValidate" @close="modalValidate = false" />
                <!-- ================ -->


              </div>
              <!-- ================ -->





              <img alt="Vue logo" src="../assets/img/vue-logo.svg" width="50" height="50">
            </article>
          </section>
        </div>

    </div>
  </div>
</template>




<script>

import notes from '@/components/Notes.vue'
import newNote from '@/components/NewNote.vue'
import search from '@/components/Search.vue'
import modals from '@/components/Modals.vue'
import modalValidate from '@/components/ModalValidate.vue'

export default {
  name: 'Sandbox',
  components: {
    newNote,
    notes,
    search,
    modals,
    modalValidate

  },
  data: () => ({
    title: 'Раздел заметок',
    text: '',
    search: '',
    grid: true,
    modalView: false,
    modalForm: {
      show: false,
      name: '',
      email: ''
    },
    modalValidate: false,

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
  computed: {
    itemsFilter () {
      let array = this.items,
          search = this.search
      if(!search) return array

      search = search.trim().toLowerCase()

      array = array.filter(function (item) {
        if (item.title.toLowerCase().indexOf(search) !==-1) {
          return item
        }
      })

      return array;
    }
  },
  methods: {
    addItem (item) {
        this.items.push(item)
      },
      removeItem (index) {
        this.items.splice(index, 1)
      },
    submitForm () {
      console.log({
        name:  this.modalForm.name,
        email: this.modalForm.email
      })
          this.modalForm.name = '',
          this.modalForm.email = ''
    }

    }
  }

</script>



<style lang="scss" >

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