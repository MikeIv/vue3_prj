<template>

  <transition name="modal">
    <div class="modal__wrapper" @click="$emit('close')">
      <div  class="modal__content modal__content--anim" @click.stop="">
        <h2 class="modal__title">{{ title }}</h2>
        <div class="modal__item-icon" @click="$emit('close')">
          <svg class="modal__icon" aria-hidden="true"
               role="presentation">
            <use xlink:href="#icon-close"></use>
          </svg>
        </div>
        <slot> Содержимое окна по умолчанию</slot>
      </div>
    </div>
  </transition>



</template>

<script>

export default {

  data: () => ({
    title: '',
    name: '',
    show: true

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

.modal__content--anim {
  animation: show 1s;
}

@keyframes show {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

.modal-enter-active {
  transition: all 0.3s ease;
}
.modal-leave-active {
  transition: all 0.3s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.modal-enter, .modal-leave-to  {
  opacity: 0;
}

.modal-enter-active.modal-enter-to .modal__content {
  transition: all 0.3s ease;
  opacity: 1;
}

.modal-leave-active.modal-leave-to .modal__content {
  transform: scale(0);
  transition: all 0.3s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}



</style>