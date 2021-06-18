<template>

  <modals @close="$emit('close')" title="Modal Form width validate">
        <slot>
          <form class="modal__form" @submit.prevent="">
            <div class="modal__form-item" :class="{ error: v$.email.$error }">
              <label class="modal__label">Email:</label>
              <p class="modal__label-error" v-if="v$.email.required">Ошибка 2</p>
              <p class="modal__label-error" v-if="v$.email.email">Напишите свой email</p>
              <input class="modal__input"
                     v-model="email"
                     :class="{ errorInput: v$.email.$error }"
                     @change="v$.email.$touch()"
              >
            </div>
            <div class="modal__form-item" :class="{ error: v$.email.$error }">
              <label class="modal__label">Email:</label>
              <p class="modal__label-error" v-if="v$.email.required">Ошибка 2</p>
              <p class="modal__label-error" v-if="v$.email.email">Напишите свой email</p>
              <input class="modal__input"
                     v-model="email"
                     :class="{ errorInput: v$.email.$error }"
                     @change="v$.email.$touch()"
                     >
            </div>
            <button class="modal__btn modal__btn--submit" type="submit">Отправить</button>
          </form>
        </slot>


  </modals>

</template>




<script>

import useVuelidate from '@vuelidate/core'
import { required, email } from '@vuelidate/validators'

import modals from '@/components/Modals.vue'

export default {
  components: {
    modals,

  },

  setup () {
    return {
      v$: useVuelidate()
    }
  },

  data: () => ({
    name: '',
    email: ''

  }),

  validations: {
      name: {
        required,

      }, // Matches this.name
      email: {
          required,
          email
        } // Matches this.contact.email

  }


}

</script>

