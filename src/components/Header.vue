<template>
  <header class="header container">
    <div class="logo">
        <router-link to="/">Портфолио</router-link>
      </div>
    <nav v-if="mobileMenu">
        <img src="../img/mobile/menu.png" alt="" @click="toggleMenu" :style="hamburger">
        <ul
          class="menu"
          :style="menu"
        >
          <router-link
            to="/"
            custom
            v-slot="{ href, route, navigate, isActive, isExactActive }"
          >
            <li
              :class="[isActive && 'router-link-active', isExactActive && 'active', 'menu__li']"
            >
              <a :href="href" class="menu__link">Главная</a>
            </li>
          </router-link>
          <router-link
            to="/about"
            custom
            v-slot="{ href, route, navigate, isActive, isExactActive }"
          >
            <li
              :class="[isActive && 'router-link-active', isExactActive && 'active', 'menu__li']"
            >
              <a :href="href" class="menu__link">Обо мне</a>
            </li>
          </router-link>
          <router-link
            to="/catalog"
            custom
            v-slot="{ href, route, navigate, isActive, isExactActive }"
          >
            <li
              :class="[isActive && 'router-link-active', isExactActive && 'active', 'menu__li']"
            >
              <a :href="href" class="menu__link">Мои работы</a>
            </li>
          </router-link>
          <router-link
            to="/contacts"
            custom
            v-slot="{ href, route, navigate, isActive, isExactActive }"
          >
            <li
              :class="[isActive && 'router-link-active', isExactActive && 'active', 'menu__li']"
            >
              <a :href="href" class="menu__link">Контакты</a>
            </li>
          </router-link>
        </ul>
      </nav>
    <nav v-else>
        <ul class="menu">
          <router-link
            to="/"
            custom
            v-slot="{ href, route, navigate, isActive, isExactActive }"
          >
            <li
              :class="[isActive && 'router-link-active', isExactActive && 'active', 'menu__li']"
            >
              <a :href="href" class="menu__link">Главная</a>
            </li>
          </router-link>
          <router-link
            to="/about"
            custom
            v-slot="{ href, route, navigate, isActive, isExactActive }"
          >
            <li
              :class="[isActive && 'router-link-active', isExactActive && 'active', 'menu__li']"
            >
              <a :href="href" class="menu__link">Обо мне</a>
            </li>
          </router-link>
          <router-link
            to="/catalog"
            custom
            v-slot="{ href, route, navigate, isActive, isExactActive }"
          >
            <li
              :class="[isActive && 'router-link-active', isExactActive && 'active', 'menu__li']"
            >
              <a :href="href" class="menu__link">Мои работы</a>
            </li>
          </router-link>
          <router-link
            to="/contacts"
            custom
            v-slot="{ href, route, navigate, isActive, isExactActive }"
          >
            <li
              :class="[isActive && 'router-link-active', isExactActive && 'active', 'menu__li']"
            >
              <a :href="href" class="menu__link">Контакты</a>
            </li>
          </router-link>
        </ul>
      </nav>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data () {
    return {
      hamburger: {
        transform: 'none'
      },
      menu: {
        transform: 'none'
      }
    }
  },
  methods: {
    toggleMenu () {
      if (this.menu.transform === 'none') {
        this.menu.transform = 'translateX(-152%)'
        this.hamburger.transform = 'rotate(90deg)'
      } else {
        this.menu.transform = 'none'
        this.hamburger.transform = 'none'
      }
    }
  },
  computed: {
    mobileMenu () {
      return document.documentElement.clientWidth < 520
    }
  }
}
</script>

<style lang="sass">
.container
  max-width: 1150px
  margin: 0 auto
.header
  height: 100px
  display: flex
  justify-content: space-between
  align-items: center
.logo
  transition: all .1s linear
  &:hover
    transform: scale(1.05)
  & > a
    font-family: 'Lobster', cursive
    font-size: 2.25em
    line-height: 30px
    font-weight: 700
    color: #ffffff
.menu
  display: flex
  &__li
    margin-right: 30px
    transition: all .1s linear
    &.active
      transform: translateY(-3px)
      & > a
        border-bottom: 2px solid #fff
        &:hover
          border-bottom: 2px solid #87baf6
    &:hover
      transform: translateY(-3px)
      color: #87baf6
    &:last-child
      margin-right: 0
  &__link
    font-size: 1.13em
    line-height: 30px
    font-weight: 400
    color: #ffffff
    transition: all .1s linear
    text-transform: uppercase
    padding-bottom: 5px
    &:hover
      border-bottom: 2px solid #87baf6
      color: #87baf6

@media screen and (max-width: 1190px)
  .container
    max-width: 900px

@media screen and (max-width: 940px)
  .container
    max-width: 728px
  .logo > a
    font-size: 1.75em
  .menu__link
    font-size: 1em

@media screen and (max-width: 748px)
  .container
    max-width: 500px
  .logo > a
    font-size: 1.5em
  .menu__li
    margin-right: 12px
  .menu__link
    font-size: .9em

@media screen and (max-width: 520px)
  .container
    max-width: 300px
  nav > img
    transition: transform .3s linear
  .header
    position: relative
  .menu
    position: absolute
    right: -150%
    top: 75%
    transition: all .3s linear
    transform: translate3d(100px, 0,0)
    &__li
      margin-right: 12px
</style>
