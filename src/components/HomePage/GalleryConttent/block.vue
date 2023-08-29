<template>
<div class="mini-gallery__flex">
  <item
    v-for="work in block.works"
    v-bind:work="work"
    v-bind:key="work.id"
  />
</div>
</template>

<script>
import item from './item'
export default {
  name: 'block',
  props: ['block'],
  components: {
    item
  }
}
</script>

<style lang="sass">

</style>
