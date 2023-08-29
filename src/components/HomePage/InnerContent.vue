<template>
  <div class="inner__content container">
    <div class="inner__text">
      <h1 class="inner__h1" >Frontend-разботка</h1>
<!--      <h1 class="inner__h1">Кроссбраузерная</h1>-->
<!--      <h1 class="inner__h1">Верстка</h1>-->
      <p class="inner__p">под все типы устройств</p>
      <h1 class="inner__h1">Адаптивная,</h1>
      <h1 class="inner__h1">Кроссбраузерная</h1>
      <h1 class="inner__h1">верстка</h1>
      <p class="inner__p">Flexbox и Grid</p>
      <h2 v-if="mobile" class="inner__h2">Верстка отдельных компонентов</h2>
      <p v-if="mobile" class="inner__p">Использование Vanilla.js, Vue.js</p>
    </div>
    <p></p>
    <p></p>
    <div class="mac-img">
      <img src="../../img/mac.png" alt="">
    </div>
    <div class="ipad-img">
      <img src="../../img/Ipad.png" alt="">
    </div>
    <div class="iphone-img">
      <img src="../../img/iphone.png" alt="">
    </div>
  </div>
</template>

<script>
export default {
  name: 'InnerContent',
  computed: {
    mobile () {
      return document.documentElement.clientWidth > 520
    }
  }
}
</script>

<style lang="sass">
.inner__content
  height: 85%
  position: relative
  text-align: right
.mac-img,
.ipad-img,
.iphone-img
  position: absolute
.mac-img
  left: -15%
  top: 21%
.ipad-img
  left: 26%
  top: 33%
  transform: scale(1.3)
.iphone-img
  top: 42%
  left: 39%
.inner
  &__content
    display: flex
    flex-direction: row-reverse
  &__text
    padding-top: 100px
    color: #ffffff
    max-width: 45%
    font-family: 'Marmelad', sans-serif
  &__h1
    font-size: 3.5em
    font-weight: 400
    margin: 15px 0
  &__p
    font-size: 1.5em
  &__h2
    margin: 10px 0
    font-size: 1.7em

@media screen and (max-width: 1190px)
  .mac-img
    transform: scale(.8)
    left: -20%
    top: 12%
  .ipad-img
    transform: scale(1.05)
    left: 28%
    top: 26%
  .iphone-img
    transform: scale(.8)
    left: 43%
    top: 35%
  .inner
    &__h1
      font-size: 2.25em
    &__p
      font-size: 1em
    &__h2
      font-size: 1.2em
    &__text
      padding-top: 110px

@media screen and (max-width: 940px)
  .mac-img
    transform: scale(.54)
    left: -38%
    top: 2%
  .ipad-img
    transform: scale(.7)
    left: 14%
    top: 20%
  .iphone-img
    transform: scale(.55)
    left: 29%
    top: 27%
  .inner
    &__h1
      font-size: 2em
      margin: 5px 0
    &__p
      font-size: .75em
    &__h2
      margin: 5px 0

@media screen and (max-width: 748px)
  .mac-img
    transform: scale(0.4)
    left: -61%
    top: -58%
  .ipad-img
    transform: scale(0.53)
    left: 7%
    top: -29%
  .iphone-img
    transform: scale(0.42)
    left: 25%
    top: -23%
  .inner
    &__text
      max-width: 40%
      padding-top: 30px
    &__h1
      font-size: 1.2em
    &__h2
      font-size: .9em

@media screen and (max-width: 520px)
  .mac-img
    transform: scale(0.25)
    left: -120%
    top: -53%
  .ipad-img
    transform: scale(0.335)
    left: -16%
    top: -24%
  .iphone-img
    transform: scale(0.25)
    left: 9%
    top: -22%
  .inner
    &__text
      padding-top: 55px
    &__h1
      font-size: .8em
    &__p
      font-size: 0.6em
</style>
