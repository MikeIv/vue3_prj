<template>

  <modals @close="$emit('close')" title="Modal Form width validate">
        <slot>
          <form class="modal__form" @submit.prevent="">
            <div class="modal__form-item" :class="{ error: v$.name.$error }">
              <label class="modal__label">Имя:</label>
              <p class="modal__label-error" v-if="!v$.name.required">Ошибка 1</p>
              <p class="modal__label-error" v-if="v$.name.minLength">Имя должно содержать не менее 4 символов</p>
              <input class="modal__input"
                     v-model="name"
                     :class="{ errorInput: v$.name.$error }"
                     @change="v$.name.$touch()"
                     required>
            </div>
            <div class="modal__form-item">
              <label class="modal__label">Email:</label>
              <input class="modal__input" v-model="contact.email">
            </div>
            <button class="modal__btn modal__btn--submit">Отправить</button>
          </form>
        </slot>


<!--    <div :class="{ error: v$.name.$errors.length }">-->
<!--      <input v-model="name">-->
<!--      <div class="input-errors" v-for="error of v$.name.$errors" :key="error.$uid">-->
<!--        <div class="error-msg">{{ error.$message }}</div>-->
<!--      </div>-->
<!--    </div>-->
  </modals>

</template>




<script>

import useVuelidate from '@vuelidate/core'
import { required, minLength, email } from '@vuelidate/validators'

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
    contact: {
      email: ''
    }
  }),

  validations: {
      name: {
        required,
        minLength: minLength(4)
      }, // Matches this.name
      contact: {
        email: {
          required,
          email
        } // Matches this.contact.email
      }

  }


}

</script>

