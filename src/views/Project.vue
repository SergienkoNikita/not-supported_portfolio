<template>
  <div>
    <HeaderLocal />
    <div class="bread-crumbs">
      <div class="container">
        <div class="bread-crumbs__content">
          <router-link to="/catalog"><i class="fa fa-arrow-left"></i>Вернуться в каталог</router-link>
          <router-link to="/">На главную<i class="fa fa-arrow-right"></i></router-link>
        </div>
      </div>
    </div>
    <loader v-if="!render"/>
    <section v-else class="project">
      <div class="container">
        <h1 class="project__title" v-html="project.title"></h1>
        <h3 v-if="project.adaptive" class="project__adaptive true">Проект адаптивный</h3>
        <h3 v-else class="project__adaptive">Проект не адаптивный</h3>
        <p class="project__text" v-html="project.text"></p>
        <a :href="project.path"  class="project__link" target="_blank">перейти на страницу проекта <i class="fas fa-chevron-right"></i></a>
      </div>
      <figure class="project__slide" @mouseover="stopAnimation" @mouseleave="startAnimation">
        <img
          :src="require(`@/img/${project.name}/`+currentSlide.big)"
          alt="">
        <p v-html="currentSlide.desc"></p>
        <i
          @click="getNextSlide"
          class="fas fa-chevron-right project__arr_right"></i>
        <i
          @click="getPrevSlide"
          class="fas fa-chevron-left project__arr_left"></i>
      </figure>
      <div class="carousel"
           @mousedown.prevent="(e) => setStart(e)"
           @mousemove="(e) => changePos(e)"
           @mouseup="savePos"
           @mouseover="stopAnimation"
           @mouseleave="startAnimation"
      >
        <div class="carousel__inner">
          <div
            :style="{left: `${current}px`, transition}"
            class="carousel__block"
            @transitionend="transition = 'none'"
          >
            <img
              v-for="photo in project.images"
              :key="photo.id"
              :src="require(`@/img/${project.name}/`+photo.small)"
              :class="{active: photo.active, image: true}"
              @click="changeSlide(photo.id)"
              alt="photo.id">
          </div>
        </div>
      </div>
    </section>
    <Footer />
  </div>
</template>

<script>

import HeaderLocal from '../components/HeaderLocal'
import Footer from '../components/Footer'
import loader from '../components/loader'
export default {
  name: 'Project',
  data () {
    return {
      project: null,
      currentSlide: {},
      render: false,
      start: null,
      active: false,
      current: 0,
      startMouse: 0,
      savedX: 0,
      transition: 'none',
      animation: null,
      similar: []
    }
  },
  components: {
    HeaderLocal,
    Footer,
    loader
  },
  props: ['id'],
  methods: {
    setStart (e) {
      this.start = e.screenX
      this.active = true
    },
    changePos (e) {
      if (this.active) {
        this.startMouse = this.savedX + (e.screenX - this.start)
        this.current = this.startMouse
        if (this.current > 50) {
          this.current = 0
        } else if (this.current < -(((document.querySelector('.image').clientWidth + 20) * this.project.images.length) - document.querySelector('.carousel__inner').clientWidth + 70)) {
          this.current = -(((document.querySelector('.image').clientWidth + 20) * this.project.images.length) - document.querySelector('.carousel__inner').clientWidth + 40)
        }
      }
    },
    savePos () {
      this.active = false
      this.savedX = this.current
    },
    getNextSlide () {
      if (this.currentSlide.id === this.project.images.length) {
        this.currentSlide = this.project.images.find(el => el.id === 1)
        this.transition = 'left .6s linear'
        this.current = 0
        this.savePos()
        this.toggleClass()
      } else {
        this.currentSlide = this.project.images.find(el => el.id === (this.currentSlide.id + 1))
        this.toggleClass()
        if (((this.currentSlide.id * (document.querySelector('.image').clientWidth + 20)) + 20) > (document.querySelector('.carousel__inner').clientWidth + Math.abs(this.current))) {
          const difference = ((this.currentSlide.id * (document.querySelector('.image').clientWidth + 20)) + 20) - (document.querySelector('.carousel__inner').clientWidth + Math.abs(this.current))
          this.transition = 'left .3s linear'
          this.current += -difference
          this.savePos()
        }
      }
    },
    getPrevSlide () {
      const l = document.documentElement.clientWidth
      console.log(l)
      if (this.currentSlide.id === 1) {
        this.currentSlide = this.project.images.find(el => el.id === this.project.images.length)
        this.transition = 'left .6s linear'
        this.current = -(((document.querySelector('.image').clientWidth + 20) * this.project.images.length) - document.querySelector('.carousel__inner').clientWidth + 40)
        this.savePos()
        this.toggleClass()
      } else {
        this.currentSlide = this.project.images.find(el => el.id === (this.currentSlide.id - 1))
        this.toggleClass()
        if (((this.currentSlide.id - 1) * (document.querySelector('.image').clientWidth + 20)) < Math.abs(this.current)) {
          const difference = Math.abs(this.current) - (this.currentSlide.id - 1) * (document.querySelector('.image').clientWidth + 20)
          this.transition = 'left .3s linear'
          this.current += difference
          this.savePos()
        }
      }
    },
    changeSlide (id) {
      this.currentSlide = this.project.images.find(el => el.id === id)
      this.toggleClass()
    },
    toggleClass () {
      this.project.images.find(el => el.active === true).active = false
      this.project.images.find(el => el.id === this.currentSlide.id).active = true
    },
    startAnimation () {
      this.animation = setInterval(() => {
        this.getNextSlide()
      }, 2000)
    },
    stopAnimation () {
      clearInterval(this.animation)
    },
    getJson (url) {
      return fetch(url)
        .then(result => result.json())
        .catch(error => {
          console.log(error)
        })
    }
  },
  mounted () {
    this.getJson(`https://raw.githubusercontent.com/brave312guide/Carousele/main/API/proj-id-${this.id}.json`).then(data => {
      this.project = data
      this.render = true
      this.currentSlide = this.project.images[0]
      this.project.images[0].active = true
      this.startAnimation()
    })
    this.getJson('https://raw.githubusercontent.com/brave312guide/Carousele/main/API/portfolio.json').then(data => {
      this.similar = data.filter(el => el.id !== parseInt(this.id))
    })
  },
  beforeDestroy () {
    this.stopAnimation()
    this.project = null
  }
}
</script>

<style lang="sass">
.project
  text-align: center
  &__title
    margin-top: 40px
    color: #3e5f7f
    font-size: 2.5em
    text-shadow: 14px 6px 7px rgba(145, 150, 145, 1)
  &__adaptive
    padding: 5px 15px
    margin: 20px auto
    background-color: #801d1d
    border-radius: 13px
    color: #ffffff
    display: inline-block
    &.true
      background-color: #067635
  &__text
    color: rgba(61, 60, 60, 0.71)
    font-size: 1.1em
    margin-bottom: 30px
  &__link
    color: #87baf6
    transition: all 0.2s linear
    text-transform: uppercase
    font-weight: 700
    display: inline-block
    margin-bottom: 30px
    &:hover
      transform: scale(1.05)
      color: #34495e
  &__slide
    max-width: 900px
    margin: 0 auto
    padding: 50px 0 15px
    background-color: #e5e5e5
    border-top-right-radius: 30px
    border-top-left-radius: 30px
    position: relative
    & > img
      box-shadow: 0 0 13px 2px rgb(34 60 80 / 20%)
    & > p
      margin-top: 20px
      font-size: 1.1em
      font-style: italic
      color: rgba(0, 0, 0, 0.58)
  &__arr_left,
  &__arr_right
    position: absolute
    top: 50%
    font-size: 2em
    color: #444444
    transition: all .2s linear
    &:hover
      cursor: pointer
      color: #000
  &__arr_left
    left: 50px
  &__arr_right
    right: 50px
.carousel
  background-color: #e5e5e5
  min-height: 280px
  padding: 60px 150px
  &__inner
    height: 190px
    position: relative
    overflow: hidden
  &__block
    position: absolute
    display: flex
    align-items: center
    height: 190px
    & > img
      margin-right: 20px
      box-shadow: 0 0 13px 2px rgb(34 60 80 / 20%)
      &:hover
        cursor: pointer
      &.active
        transform: translateY(-15px)
        box-shadow: 0 18px 8px 0 rgb(34 60 80 / 20%)
      &:first-child
        margin-left: 20px

.bread-crumbs
  background: rgb(190,197,251)
  background: linear-gradient(0deg, rgba(190,197,251,1) 0%, rgba(23,27,58,1) 88%)
  height: 50px
  &__content
    display: flex
    justify-content: space-between
    align-items: center
    height: 50px
    & > a
      color: #fff
      margin: 0 40px
      font-style: italic
      &:first-child > i
        margin-right: 10px
      &:last-child > i
        margin-left: 10px
      & > i
        font-size: .7em
@media screen and (max-width: 1190px)
  .project
    &__title
      font-size: 2.2em
    &__adaptive
      font-size: 1em
    &__text
      font-size: 1em
  .carousel
    padding: 60px 70px
@media screen and (max-width: 940px)
  .project
    &__title
      font-size: 2em
    &__slide
      max-width: 728px
      & > img
        max-width: 500px
  .carousel
    padding: 30px 50px
    min-height: 200px
    &__block,
    &__inner
      height: 150px
    &__block > img
      max-width: 250px
@media screen and (max-width: 748px)
  .project
    &__title
      font-size: 2em
    &__slide
      max-width: 500px
      & > img
        max-width: 350px
      & > p
        font-size: .9em
  .project__arr_right
    right: 25px
  .project__arr_left
    left: 25px
  .carousel
    padding: 30px 25px
    &__block,
    &__inner
      height: 120px
    &__block > img
      max-width: 200px
  .bread-crumbs__content > a
    margin: 0
    font-size: .8em
@media screen and (max-width: 520px)
  .project
    &__title
      font-size: 1.5em
    &__adaptive
      font-size: .8em
    &__text
      font-size: .8em
    &__link
      font-size: .8em
    &__slide
      max-width: 300px
      & > img
        max-width: 220px
      & > p
        font-size: .9em
  .project__arr_right
    font-size: 1em
    right: 15px
  .project__arr_left
    font-size: 1em
    left: 15px
  .carousel
    padding: 20px 0
    min-height: 130px
    &__block > img
      max-width: 150px
    &__block,
    &__inner
      height: 100px
</style>
