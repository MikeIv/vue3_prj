<template>
  <!--  note list-->
  <ul class="vue-notes">
    <li class="vue-note" :class="{ notewidth: !grid }" v-for="(item, index) in items" :key="index">
      <div class="vue-note__item-icon" @click="removeItem(index)">
        <svg class="vue-note__icon" aria-hidden="true"
             role="presentation">
          <use xlink:href="#icon-close"></use>
        </svg>
      </div>
      <p class="note-header">{{ item.title }} :grid="3"</p>
      <p class="note-body">{{ item.descr }}</p>
      <span class="note-datу">{{ item.date }}</span>
    </li>
  </ul>

</template>


<script>
export default {

  props: {
    items: {
      type: Array,
      required: true
    },
    grid: {
      type: Boolean,
      required: true,
    }

  },


  methods: {
    removeItem (index) {
      this.$emit('remove', index)

    }

  }

}



</script>


<style lang="scss">

.vue-note.notewidth {
  width: 100%;
}

</style>