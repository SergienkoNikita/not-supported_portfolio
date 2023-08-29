<template>
<section class="contacts">
  <div class="container">
    <h1 class="contacts__title">Контакты</h1>
    <p class="contacts__text">Со мной можно связаться по нижеуказанным контактам, в любой день недели с 8:00 до 22:00 По МСК</p>
    <div class="contacts__links">
      <div class="contacts__apps">
        <a class="telegram" href="https://t.me/brave_guide"><i class="fab fa-telegram"></i>@brave_guide</a>
        <a class="whatsapp" href="https://api.whatsapp.com/send?phone=380663566405&text=%D0%94%D0%BE%D0%B1%D1%80%D1%8B%D0%B9%20%D0%B4%D0%B5%D0%BD%D1%8C%2C%20%D1%8F%20%D0%BF%D0%BE%20%D0%BF%D0%BE%D0%B2%D0%BE%D0%B4%D1%83..."><i class="fab fa-whatsapp"></i> WhatsApp</a>
        <a class="viber" href="viber://chat?number=%2B380663566405"><i class="fab fa-viber"></i>+ 38 066 35 66 405</a>
      </div>
      <div class="contacts__local">
        <a class="phone" href="tel:+38 (066) 35 66 405"><i class="fas fa-mobile-alt"></i> + 38 066 35 66 405</a>
        <a class="mail" href="mailto:sergienkonikita77@gmail.com"><i class="far fa-envelope"></i>sergienkonikita77@gmail.com</a>
      </div>
  </div>
  </div>
</section>
</template>

<script>
export default {
  name: 'Contacts'
}
</script>

<style lang="sass">
.contacts
  width: 100%
  padding-top: 30px
  min-height: 400px
  background-color: #eee
  &__title
    color: #3e5f7f
    font-size: 2.5em
  &__text
    color: #3e5f7f
    font-size: 18px
    margin: 20px 0
  &__links
    display: flex
    width: 50%
    margin: 0 auto
    height: 100%
    justify-content: space-between
  &__apps,
  &__local
    display: flex
    flex-direction: column
    & > a
      margin-bottom: 10px
      font-size: 1.25em
      color: #000
      &:last-child
        margin-bottom: 0
      & > i
        margin-right: 10px
      &:hover
        color: #4d7eac
.telegram
  align-self: flex-start
.whatsapp
  align-self: flex-start
.viber
  align-self: flex-start
.phone
  align-self: flex-end
.mail
  align-self: flex-end
@media screen and (max-width: 1190px)
  .contacts__links
    width: 60%
@media screen and (max-width: 940px)
  .contacts__links
    width: 70%
@media screen and (max-width: 748px)
  .contacts__title
    font-size: 1.5em
  .contacts__text
    font-size: .9em
  .contacts__links
    width: 95%
  .contacts__apps,
  .contacts__local
    & > a
      font-size: 1em
      margin-bottom: 30px
      &:last-child
        margin-bottom: 0

@media screen and (max-width: 520px)
  .contacts__links
    flex-direction: column
  .contacts__apps
    margin-bottom: 30px
  .phone,
  .mail,
  .telegram,
  .whatsapp,
  .viber
    align-self: center
</style>
