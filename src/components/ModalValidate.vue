<template>

  <modals @close="$emit('close')" title="Modal Form width validate">
    <slot>
      <form class="modal__form" @submit.prevent="">
        <label class="modal__label">Имя:</label>
        <input type="text" class="modal__input"  required>
        <label class="modal__label">Email:</label>
        <input type="email" class="modal__input"  required>
        <button class="modal__btn modal__btn--submit">Отправить</button>
      </form>
    </slot>
  </modals>


</template>


<script>
import modals from '@/components/Modals.vue'

export default {
  components: {
    modals
  },

}

</script>