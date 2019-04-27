<template>
  <q-page class="flex flex-center">
    <div class="_demo flex column flex-start">
      <Controls />
      <q-expansion-item
        expand-separator
      >
        <template v-slot:header>
          <h6 class="q-my-sm q-mr-auto">Settings</h6>
        </template>
        <div class="q-pa-sm">
          <div class="sub-title">Row content</div>
          <div class="q-gutter-sm">
            <q-radio v-model="settings.content" val="simple" label="Simple content" />
            <q-radio v-model="settings.content" val="qitem" label="QItem" />
          </div>
        </div>
      </q-expansion-item>
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
import Controls from './Controls'

export default {
  name: 'PageIndex',
  components: { Rows, Controls },
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
