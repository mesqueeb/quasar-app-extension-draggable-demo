<template>
  <q-page class="flex flex-center">
    <div class="_demo flex column flex-start">
      <Controls />
      <Settings :settings="settings" />
      <Rows :settings="settings" />
    </div>
    <div class="_bg">
      <img class="_bg-logo" alt="Quasar logo" src="~assets/quasar-logo-full.svg">
    </div>
  </q-page>
</template>

<style lang="stylus">

._demo
  position relative
  z-index 10
  background alpha(white, .9)
  padding 10px
  min-width 100%

._bg
  position fixed
  top 0
  bottom 0
  display flex
  align-items center
// ._bg-logo

.sub-title
  padding 0 .5em
  font-weight 400

</style>

<script>
import Rows from './Rows'
import Settings from './Settings'
import Controls from './Controls'

export default {
  name: 'PageIndex',
  components: { Rows, Settings, Controls },
  data () {
    return {
      settings: {
        content: 'simple',
      },
    }
  },
  computed: {
  },
  methods: {
  },
}
</script>
