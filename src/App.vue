<template>
  <div id="app">
    <pronoun-form></pronoun-form>
  </div>
</template>

<script>
import PronounForm from './components/PronounForm.vue'

export default {
  name: 'app',
  components: {
    PronounForm
  }
}
</script>

<style lang="stylus">
@import 'assets/stylus/vars'

body
  margin 0
  color f-color
#app
  font-family font
  height 100vh
  background-color lighten(secondary, 75%)
  display flex
  justify-content center
  align-items center
</style>
