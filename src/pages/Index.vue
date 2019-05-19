<template>
  <q-page class="flex flex-center">
    <div v-if="Safari" class="q-pa-lg">
      <h6 class="text-negative q-my-sm">
        Dragging doesn't work properly in Desktop Safari
      </h6>
      <div>
        It works in <strong>Mobile Safari</strong> & Google Chrome (obviously 😃).
      </div>
      <div>
        If anyone can help me find out why, please open an <a href="https://github.com/mesqueeb/quasar-app-extension-draggable/issues">issue</a> to discuss.
      </div>
    </div>
    <div class="_demo flex column flex-start">
      <q-card>
        <q-tabs
          v-model="tabControl"
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

        <q-tab-panels v-model="tabControl" animated>
          <q-tab-panel name="controls" class="q-pa-none">
            <Controls :settings="settings" />
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
      <q-card>
        <q-tabs
          v-model="tabDemo"
          dense
          class="text-grey"
          active-color="primary"
          indicator-color="primary"
          align="justify"
          narrow-indicator
        >
          <q-tab name="simple" label="Basic Demo" />
          <q-tab name="9000" label="300 rows (slow)" />
        </q-tabs>

        <q-separator />

        <q-tab-panels v-model="tabDemo" animated>
          <q-tab-panel name="simple" class="q-pa-sm">
            <Rows :settings="settings" />
          </q-tab-panel>
          <q-tab-panel name="9000" class="q-pa-sm">
            <Rows9000 :settings="settings" />
          </q-tab-panel>
        </q-tab-panels>
      </q-card>

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
import Rows9000 from './Rows9000'
import Settings from './Settings'
import Controls from './Controls'
import Source from './Source'

export default {
  name: 'PageIndex',
  components: { Rows, Rows9000, Settings, Controls, Source },
  data () {
    return {
      Safari: this.$q.platform.is.safari && this.$q.platform.is.desktop,
      tabControl: 'controls',
      tabDemo: 'simple',
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
