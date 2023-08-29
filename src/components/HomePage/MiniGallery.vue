<template>
<section class="mini-gallery">
  <div class="container">
    <h1 class="mini-gallery__title">Последние работы</h1>
  </div>
    <div class="mini-gallery__carousel">
      <div class="mini-gallery__inner">
          <block
            v-for="block in workBlocks"
            :block="block"
            :key="block.id"
            :style="{left: block.left}"
            :class="{animationLeft: block.animationLeft, animationRight: block.animationRight}"
          />
      </div>
      <div class="mini-gallery__arrLeft" @click="moveRight"><i class="fa fa-chevron-left"></i></div>
      <div class="mini-gallery__arrRight" @click="moveLeft"><i class="fa fa-chevron-right"></i></div>
  </div>
</section>
</template>

<script>
import block from './GalleryConttent/block'
export default {
  name: 'MiniGallery',
  components: {
    block
  },
  props: ['workBlocks'],
  data () {
    return {
      current: null,
      next: null
    }
  },
  methods: {
    moveRight () {
      this.current = this.workBlocks.find(el => parseInt(el.left) === 0)
      if (this.workBlocks.length > 1) {
        if (this.current.id >= this.workBlocks.length) {
          this.current.animationLeft = true
          const vm = this
          // eslint-disable-next-line no-return-assign
          setTimeout(() => vm.current.animationLeft = false, 200)
        } else {
          this.next = this.workBlocks.find(el => el.id === this.current.id + 1)
          this.current.left = '-100%'
          this.next.left = '0'
        }
      } else {
        this.current.animationLeft = true
        const vm = this
        // eslint-disable-next-line no-return-assign
        setTimeout(() => vm.current.animationLeft = false, 200)
      }
    },
    moveLeft () {
      this.current = this.workBlocks.find(el => parseInt(el.left) === 0)
      if (this.workBlocks.length > 1) {
        if (this.current.id <= 1) {
          this.current.animationRight = true
          const vm = this
          // eslint-disable-next-line no-return-assign
          setTimeout(() => vm.current.animationRight = false, 200)
        } else {
          this.next = this.workBlocks.find(el => el.id === this.current.id - 1)
          this.current.left = '100%'
          this.next.left = '0'
        }
      } else {
        this.current.animationRight = true
        const vm = this
        // eslint-disable-next-line no-return-assign
        setTimeout(() => vm.current.animationRight = false, 200)
      }
    }
  }
}
</script>

<style lang="sass">
.mini-gallery
  padding: 75px 0
  background-color: #eeeeee
  text-align: center
  width: 100%
  margin-bottom: 150px
  &__title
    font-size: 2.25em
    font-weight: 700
    letter-spacing: -0.01em
    color: #34495e
    margin-bottom: 20px
  &__carousel
    width: 100%
    height: 300px
    position: relative
    background-color: #e5e5e5
  &__arrLeft,
  &__arrRight
    position: absolute
    top: 45%
    color: #34495e
    font-size: 30px
    &:hover
      cursor: pointer
  &__arrLeft
    left: 13%
  &__arrRight
    right: 13%
  &__inner
    width: 70%
    height: 100%
    margin: 0 15%
    overflow: hidden
    position: relative
    display: flex
  &__flex
    width: 100%
    height: 100%
    display: flex
    justify-content: space-between
    position: absolute
    transition: left .6s linear
    &.animationLeft
      transform: translateX(-5px)
    &.animationRight
      transform: translateX(5px)

@media screen and (max-width: 1190px)
  .mini-gallery__arrLeft
    left: 10%
  .mini-gallery__arrRight
    right: 10%

@media screen and (max-width: 748px)
  .mini-gallery
    padding-top: 40px
    &__carousel
      height: 200px

@media screen and (max-width: 520px)
  .mini-gallery
    &__title
      font-size: 1.5em
    &__flex
      flex-direction: column
      align-items: center
    &__carousel
      height: 500px
  .mini-gallery__arrLeft
    left: 7%
  .mini-gallery__arrRight
    right: 7%
</style>
