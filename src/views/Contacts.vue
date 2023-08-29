<template>
  <div class="contacts-page">
    <HeaderLocal />
    <ContactsBlock />
    <Footer />
  </div>
</template>

<script>
import HeaderLocal from '../components/HeaderLocal'
import Footer from '../components/Footer'
import ContactsBlock from '../components/Contacts/ContactsBlock'
export default {
  name: 'Contacts',
  components: {
    HeaderLocal,
    Footer,
    ContactsBlock
  }
}
</script>

<style lang="sass">
.contacts-page
  display: grid
  height: 100vh
  grid-template-rows: auto 1fr auto
  background-color: #eee
  text-align: center
</style>
