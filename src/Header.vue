<template>
  <header class="header-pages">

    <div class="header__page-wrapper">
      <a href="/">
        <img src="./assets/img/my-logo.svg" alt="logo" class="header__main-logo">
      </a>
      <div class="header__left-line"></div>
      <nav class="page-nav">
        <ul class="page-nav__list">
          <li class="page-nav__item"><router-link to="/portfolio" exact class="main-nav__link">Портфолио</router-link></li>
          <li class="page-nav__item"><router-link to="/tools" exact class="main-nav__link">Инструменты</router-link></li>
          <li class="page-nav__item"><router-link to="/sandbox" exact class="main-nav__link">Песочница</router-link></li>
          <li class="page-nav__item"><router-link to="/contacts" exact class="main-nav__link">Контакты</router-link></li>
        </ul>
      </nav>

    </div>


  </header>
</template>

<script>
export default {
  name: "Header",

  data: () => ({
    isActive: false,
    activeClass: 'active'

  }),

  computed: {
    activePage: function () {
      return {
        active: this.isActive && !this.error
      }
    }
  }
}
</script>

<style lang="scss" scoped>


</style>