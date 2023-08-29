<template>
  <div>
    <HeaderLocal />
    <Summary />
    <Skills />
    <Additionally/>
    <Footer />
  </div>
</template>

<script>
import HeaderLocal from '../components/HeaderLocal'
import Summary from '../components/About/Summary'
import Skills from '../components/About/Skills'
import Footer from '../components/Footer'
import Additionally from '../components/About/Additionally'

export default {
  name: 'About',
  components: {
    HeaderLocal,
    Summary,
    Skills,
    Footer,
    Additionally
  }
}
</script>

<style lang="sass">

</style>
