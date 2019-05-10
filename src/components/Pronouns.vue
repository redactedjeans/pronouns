<template>
  <div class="input">
    <span class="pronoun"><input type="text" class=""></span>
    <span class="pronoun"><input type="text" class=""></span>
    <span class="pronoun"><input type="text" class=""></span>
  </div>
</template>

<script>
export default {
    name: 'Pronouns'
}
</script>

<style lang="stylus" scoped>
@import '../assets/stylus/vars'

// pronoun field
.pronoun
  // input element
  input
    box-sizing border-box
    width (100 / 3)%
    background none
    border none
  // separators
  &:not(:last-child)
    position relative
    input
      padding-right 1rem
    &::after
      position absolute
      right 0.5rem
      content '/'
      font-size 1.2rem
      color lighten(f-color, 50%)
</style>