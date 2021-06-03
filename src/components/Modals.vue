<template>


    <div class="modal__wrapper" @click="$emit('close')">
      <transition name="modal">
      <div class="modal__content" @click.stop="">
        <h2 class="modal__title">{{ title }}</h2>
        <div class="modal__item-icon" @click="$emit('close')">
          <svg class="modal__icon" aria-hidden="true"
               role="presentation">
            <use xlink:href="#icon-close"></use>
          </svg>
        </div>
        <slot> Содержимое окна по умолчанию</slot>
      </div>
      </transition>
    </div>



</template>

<script>

export default {

  data: () => ({
    title: 'Модальное окно',

  }),

  mounted() {
    document.body.addEventListener('keyup', e => {
      if(e.keyCode === 27) this.$emit('close')
    })
  },

  copmuted: {

  },
  methods: {

  }
}

</script>

<style lang="scss">

.modal-enter-active {
  transition: all 1s ease;
}

.modal-leave-active {
  transition: all 1s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}

.modal-enter, .modal-leave-to {
  transform: translateX(40rem);
  opacity: 0;
}

</style>