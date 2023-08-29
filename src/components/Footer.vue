<template>
<footer class="footer">
  <div class="footer__contact container">
    <SocialLinks />
    <a href="mailto:sergienkonikita77@gmail.com"><i class="far fa-envelope"></i>sergienkonikita77@gmail.com</a>
  </div>
  <div class="footer__bottom">
    <div class="container">
      {{ year.getFullYear() }} Sergienko Nikita
    </div>
  </div>
</footer>
</template>

<script>
import SocialLinks from './SocialLinks'
export default {
  name: 'Footer',
  components: {
    SocialLinks
  },
  computed: {
    year () {
      return new Date()
    }
  }
}
</script>

<style lang="sass">
.footer
  background-color: #34495e
  &__contact
    display: flex
    align-items: center
    justify-content: space-between
    padding: 30px 0
    & > ul > li > a
      color: #fff
      &:hover
        color: #87baf6
        transition: color .1s linear
    & > a
      color: #fff
      transition: color .1s linear
      & > i
        margin-right: 10px
        font-size: 15px
      &:hover
        color: #87baf6
  &__bottom
    color: #fff
    text-align: center
    font-style: oblique
    padding: 20px 0
    background-color: #2c3e50
    position: relative
    border-top: 1px solid #183749
    &:before
      content: ""
      height: 20px
      width: 20px
      background-color: #2c3e50
      position: absolute
      top: -11px
      left: 50%
      transform: rotate(45deg)
      border-top: 1px solid #183749
      border-left: 1px solid #183749

@media screen and (max-width: 520px)
  .footer__contact
    flex-direction: column-reverse
    justify-content: space-between
  .footer__contact > ul > li > a
    font-size: 1.8em
  .footer__contact > a
    margin-bottom: 20px
    font-size: 1em
    & > i
      font-size: 1em
  .footer__bottom:before
    left: 46%
</style>
