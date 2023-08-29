<template>
  <div class="summary container">
    <div class="summary__content">
      <h1 class="summary__h1">Сергиенко Никита Дмитриевич</h1>
      <h4 class="summary__h4">Дата рождения: 31 марта 1995, 26 лет</h4>
      <h4 class="summary__h4">Место жительства: Донецк (Краснодар, Ростов-на-Дону)</h4>
      <a href="mailto:sergienkonikita77@gmail.com"><i class="far fa-envelope"></i>sergienkonikita77@gmail.com</a>
      <SocialLinks />
      <h2 class="summary__h2">Frontend-разработчик</h2>
    </div>
    <img src="../../img/summary-photo.jpg" alt="Photo" class="summary-photo">
  </div>
</template>

<script>
import SocialLinks from '../SocialLinks'
export default {
  name: 'Summary',
  components: {
    SocialLinks
  }
}
</script>

<style lang="sass">
.summary
  display: flex
  justify-content: space-between
  padding: 80px 0 0
  width: 100%
  &__h1
    margin: 30px 0
  &__h4
    color: rgba(61, 60, 60, 0.71)
    margin-bottom: 20px
  &__content > a
    color: #87baf6
    transition: color .1s linear
    & > i
      margin-right: 10px
    &:hover
      color: #3e5f7f
  &__content > ul
    margin-top: 10px
  &__h2
    margin-top: 40px
    color: #3e5f7f
    font-size: 2.5em
  &-photo
    border-radius: 50%
    border: 2px solid #0f5086
    padding: 2px

@media screen and (max-width: 940px)
  .summary
    &__h1
      font-size: 1.75em
      margin: 20px 0
    &__h4
      margin-bottom: 15px
      font-size: 1em
    &__h2
      margin-top: 50px
      font-size: 2em
    &-photo
      height: 250px
      margin-top: 20px

@media screen and (max-width: 748px)
  .summary
    &__h1
      font-size: 1.3em
    &__h4
      font-size: .8em
      letter-spacing: -.03em
    &-photo
      height: 200px
      margin-top: 20px

@media screen and (max-width: 520px)
  .summary-photo
    height: 175px
  .summary__h2
    display: none
  .summary__content > a
    font-size: .8em
    & > i
      margin-right: 5px
</style>
