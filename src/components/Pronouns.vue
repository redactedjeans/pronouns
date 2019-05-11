<template>
  <div class="form-grp optional">
    <label class="form-grp-label" for="pronouns">Pronouns</label>
    <div class="form-grp-descr">Leave this empty if you want to use your name.</div>
    <div class="input">
      <span class="pronoun"><input v-model="subRaw" type="text" class=""></span>
      <span class="pronoun"><input v-model="objRaw" type="text" class=""></span>
      <span class="pronoun"><input v-model="posRaw" type="text" class=""></span>
    </div>

    <div class="ex">
      <!-- all passages are adapted from chapter 32 of Moby Dick -->
      <div class="phrase">
        On the subject of whales, <span class="ex-prn sub">{{ sub }}</span> {{ sub=='they' ? 'are' : 'is' }} the best existing authority.
      </div>
      <div class="phrase">
        This would certainly be very convenient to <span class="ex-prn obj">{{ obj }}</span> for reading.
      </div>
      <div class="phrase">
        All of <span class="ex-prn pos">{{ pos }}</span> peculiarities will, in other places, be enlarged upon.
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Pronouns',
  props: [
    'name'
  ],
  data () {
    return {
      subRaw: '',
      objRaw: '',
      posRaw: ''
    }
  },
  computed: {
    sub: function() {
      let prn = this.subRaw.trim().toLowerCase()
      if (!prn) {
        return this.name ? this.name : '-'
      } else {
        return prn
      }
    },
    obj: function() {
      let prn = this.objRaw.trim().toLowerCase()
      if (!prn) {
        return this.name ? this.name : '-'
      } else {
        return prn
      }
    },
    pos: function() {
      let prn = this.posRaw.trim().toLowerCase()
      if (!prn) {
        return this.name ? this.name + "'s" : '-'
      } else {
        return prn
      }
    },
  }
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

// examples
.ex
  //
  .phrase
    margin-top (gutter / 2)
  .ex-prn
    font-weight bold
    color primary
</style>