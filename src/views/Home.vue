<template>
  <div>
    <inner />
    <AboutBlock />
    <MiniGallery
    :workBlocks="workBlocks"
    />
    <Footer />
  </div>
</template>

<script>
// @ is an alias to /src
import Inner from '../components/HomePage/Inner.vue'
import AboutBlock from '../components/HomePage/AboutBlock'
import MiniGallery from '../components/HomePage/MiniGallery'
import Footer from '../components/Footer'

export default {
  name: 'Home',
  data () {
    return {
      workBlocks: []
    }
  },
  components: {
    Inner,
    AboutBlock,
    MiniGallery,
    Footer
  },
  methods: {
    addBlock (id, works) {
      const block = {
        id: id,
        left: '100%',
        animationLeft: false,
        animationRight: false,
        works: works
      }
      this.workBlocks.push(block)
    }
  },
  mounted () {
    this.$parent.getJson().then(data => {
      data.reverse()
      const works = []
      for (let i = 0; i < Math.ceil(data.length / 3); i++) {
        works.push(data.slice((i * 3), (i * 3) + 3))
        if (works.length === 3) break
      }
      works.forEach((el, index) => this.addBlock(index + 1, el))
      this.workBlocks[0].left = '0'
    })
  }
}
</script>
