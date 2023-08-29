<template>
  <ul class="about-block__social">
    <li><a href="https://t.me/brave_guide"><i class="fab fa-telegram"></i></a></li>
    <li><a href="https://github.com/brave312guide"><i class="fab fa-github"></i></a></li>
    <li><a href="https://api.whatsapp.com/send?phone=380663566405&text=%D0%94%D0%BE%D0%B1%D1%80%D1%8B%D0%B9%20%D0%B4%D0%B5%D0%BD%D1%8C%2C%20%D1%8F%20%D0%BF%D0%BE%20%D0%BF%D0%BE%D0%B2%D0%BE%D0%B4%D1%83..."><i class="fab fa-whatsapp"></i></a></li>
  </ul>
</template>

<script>
export default {
  name: 'SocialLinks'
}
</script>

<style lang="sass">
.about-block__social
  display: flex
  margin-top: 20px
  & > li
    margin-right: 20px
    transition: color .1s linear
    &:active
      transform: scale(.9)
  & > li > a
    font-size: 2.5em
    color: #87baf6
    transition: color .1s linear
    &:hover
      color: #34495e
    &:active
      color: #ccc
@media screen and (max-width: 748px)
  .about-block__social
    justify-content: center
</style>
