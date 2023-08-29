<template>
<div
  :class="{item, active}"
  @mouseenter="setStyle"
  @mouseleave="setTop"
>
  <img
    :src="require('@/img/'+work.imgBig)"
    :alt="work.name"
    :id="work.name"
    :style="{top, transition}"
  >
  <div class="item__content" @mouseover.prevent>
    <div class="item__h3">&laquo;{{ work.name }}&raquo;</div>
    <router-link
      :to="{name: 'Project', params: {id: work.id}}"
    >Подробнее</router-link>
  </div>
</div>
</template>

<script>
export default {
  name: 'item',
  props: ['work'],
  data () {
    return {
      item: true,
      active: false,
      top: 0,
      transition: 'none'
    }
  },
  methods: {
    setStyle () {
      this.transition = `top ${document.getElementById(`${this.work.name}`).clientHeight / 400}s linear`
      this.top = `-${document.getElementById(`${this.work.name}`).clientHeight - this.blockHeight}px`
      this.active = true
    },
    setTop () {
      this.top = '0'
      this.transition = 'none'
      this.active = false
    }
  },
  computed: {
    blockHeight () {
      if (document.documentElement.clientWidth < 748) {
        if (document.documentElement.clientWidth < 520) {
          return 150
        } else {
          return 175
        }
      } else {
        return 280
      }
    }
  }
}
</script>

<style lang="sass">
.item
  margin: 10px 0
  height: 279px
  width: 30%
  overflow: hidden
  position: relative
  box-shadow: -1px 2px 8px 0px rgb(0 0 0 / 20%)
  & > img
    width: 100%
    position: absolute
    left: 0
.item:hover > .item__content
  display: block
.item.active > img
  filter: brightness(70%)
.item__content
  position: absolute
  height: 100%
  width: 100%
  top: 0
  left: 0
  padding: 10% 5% 0
  display: none
  text-align: left
  & > a
    display: inline-block
    margin-top: 50%
    text-align: left
    color: #fff
    font-style: italic
    font-weight: 500
    border-bottom: 1px solid #fff
    padding-bottom: 5px
    margin-left: 10px
    &:hover
      color: #c0daf8
      border-bottom: 1px solid #c0daf8
.item__h3
  font-size: 2em
  text-align: right
  color: #fff
  text-transform: uppercase

@media screen and (max-width: 1190px)
  .item__content > a
    margin-top: 80%
  .item__h3
    font-size: 1.7em

@media screen and (max-width: 940px)
  .item__h3
    font-size: 1.5em

@media screen and (max-width: 748px)
  .item__h3
    font-size: 1.1em
  .item__content > a
    font-size: .8em
  .item
    height: 175px

@media screen and (max-width: 520px)
  .item__content > a
    margin-top: 20%
  .item
    height: 150px
    width: 95%
</style>
