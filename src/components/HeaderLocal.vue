<template>
  <div class="top">
    <Header />
  </div>
</template>

<script>
import Header from './Header'
export default {
  name: 'HeaderLocal',
  components: {
    Header
  }
}
</script>

<style lang="sass">
.top
  background-color: #171b3a
@media screen and (max-width: 520px)
  .top
    overflow: hidden
    height: 130px
</style>
