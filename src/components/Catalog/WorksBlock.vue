<template>
<section class="catalog container">
  <h1 class="catalog__title">Мои работы</h1>
  <Block
    v-for="block in worksBlocks"
    :style="{display: block.display}"
    :key="block.id"
    :block="block"
  />
  <ul
    v-if="worksBlocks.length > 1"
    class="catalog__nav">
    <li @click="changePage(getPrev())"><i class="fas fa-chevron-left"></i></li>
    <li
      v-for="block in worksBlocks"
      :key="block.id"
      @click="changePage(block.id)"
    >{{ block.id }}</li>
    <li @click="changePage(getNext())"><i class="fas fa-chevron-right"></i></li>
  </ul>
</section>
</template>

<script>
import Block from './Block'
export default {
  name: 'WorksBlock',
  props: ['worksBlocks'],
  components: {
    Block
  },
  data () {
    return {
      activeBlock: null
    }
  },
  methods: {
    changePage (id) {
      this.worksBlocks.find(el => el.display === 'flex').display = 'none'
      this.worksBlocks.find(el => el.id === id).display = 'flex'
    },
    getNext () {
      if (this.worksBlocks.find(el => el.display === 'flex').id === this.worksBlocks.length) {
        return this.worksBlocks.find(el => el.display === 'flex').id
      } else {
        return this.worksBlocks.find(el => el.display === 'flex').id + 1
      }
    },
    getPrev () {
      if (this.worksBlocks.find(el => el.display === 'flex').id === 1) {
        return this.worksBlocks.find(el => el.display === 'flex').id
      } else {
        return this.worksBlocks.find(el => el.display === 'flex').id - 1
      }
    }
  }
}
</script>

<style lang="sass">
.catalog
  width: 100%
  height: 100%
  padding: 30px 0 50px
  display: flex
  flex-direction: column
  &__block
    display: flex
    flex-wrap: wrap
    justify-content: center
    & > .catalog__item:nth-child(odd)
      margin-right: 50px
    & > .catalog__item:last-child
      margin-right: 0
  &__title
    color: #3e5f7f
    font-size: 2.5em
    width: 100%
    margin-bottom: 50px
  &__nav
    display: flex
    align-self: flex-end
    & > li
      margin-right: 30px
      font-size: 20px
      font-weight: 700
      & > i
        font-size: 15px
      &:hover
        cursor: pointer
        color: #3e5f7f
@media screen and (max-width: 748px)
  .catalog__block
    display: flex
    flex-wrap: wrap
    justify-content: center
    & > .catalog__item:nth-child(odd)
      margin-right: 0
</style>
