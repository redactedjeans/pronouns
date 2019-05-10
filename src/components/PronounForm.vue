<template>
  <form class="form">
    <div class="form-grp required">
      <label class="form-grp-label" for="name">Name</label>
      <div class="form-grp-descr">Don't worry, you can change this later!</div>
      <input type="text" name="name" id="name" class="input" required>
    </div>
    <div class="form-grp optional">
      <label class="form-grp-label" for="pronouns">Pronouns</label>
      <div class="form-grp-descr">Leave this empty if you want to use your name.</div>
      <pronouns></pronouns>
    </div>
    <div style="display:flex;">
      <div style="flex:1">
        Here are some sample sentences using your selected pronouns.
      </div>
      <div style="flex:2">
        <div><span class="sub"></span> is interested in your book.</div>
        <div>Send <span class="obj"></span> a message.</div>
        <div>This is <span class="pos"></span> fifth loan.</div>
      </div>
    </div>
    <div class="form-grp form-btns">
      <button class="btn btn-reset" type="reset">Cancel</button>
      <button class="btn btn-submit" type="submit">Gender is fake</button>
    </div>
  </form>
</template>

<script>
import Pronouns from './Pronouns.vue'

export default {
  name: 'PronounForm',
  components: {
    Pronouns
  }
}
</script>

<style lang="stylus" scoped>
@import '../assets/stylus/vars'

// form wrapper
.form
  position relative
  top -(gutter * 10)
  min-width 300px
  max-width 500px
  background-color white
  padding (gutter * 2)
  border-radius (round * 2)
  border-right  bw solid secondary
  border-bottom bw solid secondary

  // input group
  &-grp
    width 100%
    display flex
    flex-direction column
    margin-bottom (gutter * 2)
    &:last-child
      margin-bottom 0
    // group description
    &-descr
      font-size small
      margin-bottom (gutter / 2)
    // required group labels
    &-label::after
      color primary
      font-style italic
      font-size small 
    &.required &-label::after
      content ' *'
    &.optional &-label::after
      content ' (optional)'
  // input group of buttons
  &-btns
    flex-direction row
    justify-content end

.ex .ex-pro
  font-weight bold
  color primary

// button input
.btn
  cursor pointer
  border none
  padding gutter
  border-radius round
  margin-left gutter
  &-reset
    background-color secondary
    &:active
      background-color darken(secondary, diff)
  &-submit
    background-color primary 
    color white
    font-weight bold
    &:active
      background-color darken(primary, diff)

// text input
.input
  padding gutter
  border none
  border-bottom bw solid primary 
  background-color lighten(secondary, 75%)
  transition background-color time func
  // focused input
  &:focus,
  &:focus-within
    background-color lighten(secondary, 50%)
</style>
