<template>
  <!--  note list-->
  <div class="vue-notes">
    <div class="vue-note" v-for="(note, index) in notes" :key="index" :class="{ notewidth: !grid }">
      <div class="vue-note__item-icon" @click="removeCard(index)">
        <svg class="vue-note__icon" aria-hidden="true"
             role="presentation">
          <use xlink:href="#icon-close"></use>
        </svg>
      </div>
        <p class="note-header">{{ note.title }}</p>
        <p class="note-body">{{ note.descr }}</p>
        <span class="note-datу">{{ note.date }}</span>
    </div>
  </div>

</template>


<script>


</script>


<style lang="scss">

.vue-note.notewidth {
  width: 100%;
}

</style>