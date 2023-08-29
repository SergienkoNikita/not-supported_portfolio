<template>
  <div class="loader">
    <h2>Подождите загрузку контента</h2>
    <div class="snippet" data-title=".dot-falling">
      <div class="stage">
        <div class="dot-falling"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'loader'
}
</script>

<style lang="sass">
.loader
  display: flex
  width: 100%
  justify-content: center
  align-items: center
  height: 62vh
  & > h2
    margin-right: 30px
    color: #5427dc
.dot-falling
  position: relative
  left: -9999px
  width: 10px
  height: 10px
  border-radius: 5px
  background-color: #5427dc
  color: #5427DCFF
  box-shadow: 9999px 0 0 0 #5427DCFF
  animation: dotFalling 1s infinite linear
  animation-delay: .1s
.dot-falling::before, .dot-falling::after
  content: ''
  display: inline-block
  position: absolute
  top: 0
.dot-falling::before
  width: 10px
  height: 10px
  border-radius: 5px
  background-color: #5427DCFF
  color: #5427DCFF
  animation: dotFallingBefore 1s infinite linear
  animation-delay: 0s
.dot-falling::after
  width: 10px
  height: 10px
  border-radius: 5px
  background-color: #5427DCFF
  color: #5427DCFF
  animation: dotFallingAfter 1s infinite linear
  animation-delay: .2s
@keyframes dotFalling
  0%
    box-shadow: 9999px -15px 0 0 rgba(152, 128, 255, 0)

  25%,
  50%,
  75%
    box-shadow: 9999px 0 0 0 #5427DCFF
  100%
    box-shadow: 9999px 15px 0 0 rgba(152, 128, 255, 0)
@keyframes dotFallingBefore
  0%
    box-shadow: 9984px -15px 0 0 rgba(152, 128, 255, 0)
  25%,
  50%,
  75%
    box-shadow: 9984px 0 0 0 #5427DCFF
  100%
    box-shadow: 9984px 15px 0 0 rgba(152, 128, 255, 0)
@keyframes dotFallingAfter
  0%
    box-shadow: 10004px -15px 0 0 rgba(152, 128, 255, 0)
  25%,
  50%,
  75%
    box-shadow: 10004px 0 0 0 #5427DCFF
  100%
    box-shadow: 10004px 15px 0 0 rgba(152, 128, 255, 0)

@media screen and (max-width: 748px)
  .loader > h2
    font-size: 1em
    margin-right: 13px
  .dot-falling
    width: 7px
    height: 7px
    &:before,
    &:after
      width: 7px
      height: 7px
  @keyframes dotFallingBefore
    0%
      box-shadow: 9988px -15px 0 0 rgba(152, 128, 255, 0)
    25%,
    50%,
    75%
      box-shadow: 9988px 0 0 0 #5427DCFF
    100%
      box-shadow: 9988px 15px 0 0 rgba(152, 128, 255, 0)

@media screen and (max-width: 520px)
  @keyframes dotFallingAfter
    0%
      box-shadow: 10002px -15px 0 0 rgba(152, 128, 255, 0)
    25%,
    50%,
    75%
      box-shadow: 10002px 0 0 0 #5427DCFF
    100%
      box-shadow: 10002px 15px 0 0 rgba(152, 128, 255, 0)
</style>
