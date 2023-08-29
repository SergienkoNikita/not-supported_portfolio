<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>

export default {
  methods: {
    getJson () {
      return fetch('https://raw.githubusercontent.com/brave312guide/Carousele/main/API/portfolio.json')
        .then(result => result.json())
        .catch(error => {
          console.log(error)
        })
    }
  }
}
</script>
<style lang="sass">
#app
  font-family: 'Roboto Condensed', sans-serif
  background-color: #fff

*
  margin: 0
  padding: 0
  box-sizing: border-box
  &:focus
    outline: none
a
  text-decoration: none

li
  list-style-type: none

h1,
h2,
h3,
h4,
h5,
h6,
div,
p
  &:hover
    cursor: context-menu
  &::selection
    color: #87baf6
    background-color: #0c1a24

</style>
