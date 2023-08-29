<template>
  <div class="inner">
    <Header />
    <InnerContent />
  </div>
</template>

<script>
import Header from '../Header.vue'
import InnerContent from './InnerContent'
export default {
  name: 'Inner',
  components: {
    Header, InnerContent
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass">
.inner
  background-image: linear-gradient(0deg, rgba(255,255,255,1) 0%, rgba(0,0,0,0.6615021008403361) 10%), url(../../img/inner-bg.jpg)
  background-repeat: no-repeat
  background-size: cover
  background-position: bottom
  height: 750px

@media screen and (max-width: 1190px)
  .inner
    height: 625px
    background-image: linear-gradient(0deg, rgba(255,255,255,1) 0%, rgba(0,0,0,0.6615021008403361) 10%), url(../../img/1024px/inner-bg-1024.jpg)

@media screen and (max-width: 940px)
  .inner
    height: 500px

@media screen and (max-width: 748px)
  .inner
    height: 300px
@media screen and (max-width: 520px)
  .inner
    overflow: hidden
</style>
