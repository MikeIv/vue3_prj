<template>
  <div class="modal__wrapper" @click="$emit('close')">
    <div class="modal__content" @click.stop="">
      <h2 class="modal__title">{{ title }}</h2>
      <div class="modal__item-icon" @click="$emit('close')">
        <svg class="modal__icon" aria-hidden="true"
             role="presentation">
          <use xlink:href="#icon-close"></use>
        </svg>
      </div>
      <slot name="content"> Содержимое окна</slot>
    </div>
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