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
      <div><span class="ex-prn sub">{{ sub }}</span> {{sub.toLowerCase()=='they'?'are':'is'}} interested in your book.</div>
      <div>Send <span class="ex-prn obj">{{ obj }}</span> a message.</div>
      <div>This is <span class="ex-prn pos">{{ pos }}</span> fifth loan.</div>
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
      let prn = this.subRaw.trim()
      if (!prn) {
        return this.name ? this.name : '-'
      } else {
        return prn.charAt(0).toUpperCase() + prn.slice(1)
      }
    },
    obj: function() {
      let prn = this.objRaw.trim()
      if (!prn) {
        return this.name ? this.name : '-'
      } else {
        return prn
      }
    },
    pos: function() {
      let prn = this.posRaw.trim()
      if (!prn) {
        return this.name ? this.name : '-'
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
.ex .ex-prn
  font-weight bold
  color primary
</style>