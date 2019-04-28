<template>
  <q-page class="flex flex-center">
    <div class="_demo flex column flex-start">
      <q-card>
        <q-tabs
          v-model="tab"
          dense
          class="text-grey"
          active-color="primary"
          indicator-color="primary"
          align="justify"
          narrow-indicator
        >
          <q-tab name="controls" label="Controls" />
          <q-tab name="settings" label="Settings" />
          <q-tab name="source" label="View source" />
        </q-tabs>

        <q-separator />

        <q-tab-panels v-model="tab" animated>
          <q-tab-panel name="controls" class="q-pa-none">
            <Controls />
          </q-tab-panel>
          <q-tab-panel name="settings">
            <Settings :settings="settings" />
          </q-tab-panel>
          <q-tab-panel name="source">
            <Source :settings="settings" />
          </q-tab-panel>
        </q-tab-panels>
      </q-card>
      <div class="q-pt-lg"></div>
      <Rows :settings="settings" />
    </div>
    <!-- <div class="_bg">
      <img class="_bg-logo" alt="Quasar logo" src="~assets/quasar-logo-full.svg">
    </div> -->
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
import Source from './Source'

export default {
  name: 'PageIndex',
  components: { Rows, Settings, Controls, Source },
  data () {
    return {
      tab: 'controls',
      settings: {
        rowsRef: null,
        content: 'simple',
        selectionIndicator: 'default',
        selectionBehaviour: 'default'
      },
    }
  },
  computed: {
  },
  methods: {
  },
}
</script>
