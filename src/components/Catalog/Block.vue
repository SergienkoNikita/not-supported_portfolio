<template>
  <div class="catalog__block">
    <CatalogItem
      v-for="item in block.works"
      :key="item.id"
      :item="item"
      :bigImg="item.imgCatalogBig"
      :variantsBig="item.variantsBig"
    />
  </div>
</template>

<script>
import CatalogItem from './CatalogItem'
export default {
  name: 'Block',
  props: ['block'],
  components: {
    CatalogItem
  }
}
</script>

<style scoped>

</style>
