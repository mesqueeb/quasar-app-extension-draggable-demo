<template>
  <div>
    <h6 class="q-my-sm q-mx-md">Demo</h6>
    <q-draggable-rows
      v-model="rowsOrder"
      ref="rowsRef"
    >
      <q-draggable-row
        v-for="rowId in rowsOrder"
        :id="rowId"
        v-model="rows[rowId].depth"
        :hold-to-select="settings.selectionBehaviour === 'hold'"
        :key="rowId"
      >
        <!-- @held="notify('held', rowId)" -->
        <!-- @click.native="notify('tapped', rowId)" -->
        <Row
          :body="rows[rowId].body"
          :id="rowId"
          :settings="settings"
          slot-scope="{selected}"
          :selected="selected"
        />
        <template v-slot:selection-indicator v-if="settings.selectionIndicator === 'qcard'">
          <q-card />
        </template>
      </q-draggable-row>
    </q-draggable-rows>
  </div>
</template>

<style lang="stylus">
@import '~quasar-variables'

</style>

<script>
import Row from './Row'
export default {
  name: 'Rows',
  components: { Row },
  props: {
    settings: Object,
  },
  mounted () { this.settings.rowsRef = this.$refs.rowsRef },
  data () {
    return {
      rowsOrder: [
        'overacceleration',
        'crunchable',
        'increasedly',
        'nova',
        'oracles',
        'introject',
        'elaborating',
        'middle',
        'muff',
        'dibai',
        'music',
        'prewelcome',
        'swelteringly',
        'unvivid',
        'suttner',
        'pashim',
        'stilton',
        'beret',
        'faller',
        'cambyses',
        'clodpole',
        'emasculation',
        'obtain',
        'tackiness',
        'hac',
        'alternativity',
        'campong',
        'clamorousness',
        'presubmit',
      ],
      rows: {
        overacceleration: {id: 'overacceleration', depth: 0, body: 'Overacceleration'},
        crunchable: {id: 'crunchable', depth: 0, body: 'Crunchable'},
        increasedly: {id: 'increasedly', depth: 1, body: 'Increasedly'},
        nova: {id: 'nova', depth: 2, body: 'Nova'},
        oracles: {id: 'oracles', depth: 1, body: 'Oracles'},
        introject: {id: 'introject', depth: 0, body: 'Introject'},
        dibai: {id: 'dibai', depth: 0, body: 'Dibai'},
        pashim: {id: 'pashim', depth: 0, body: 'Pashim'},
        swelteringly: {id: 'swelteringly', depth: 0, body: 'Swelteringly'},
        elaborating: {id: 'elaborating', depth: 0, body: 'Elaborating'},
        middle: {id: 'middle', depth: 0, body: 'Middle'},
        muff: {id: 'muff', depth: 0, body: 'Muff'},
        prewelcome: {id: 'prewelcome', depth: 0, body: 'Prewelcome'},
        unvivid: {id: 'unvivid', depth: 0, body: 'Unvivid'},
        suttner: {id: 'suttner', depth: 0, body: 'Suttner'},
        stilton: {id: 'stilton', depth: 0, body: 'Stilton'},
        beret: {id: 'beret', depth: 0, body: 'Beret'},
        faller: {id: 'faller', depth: 0, body: 'Faller'},
        clodpole: {id: 'clodpole', depth: 0, body: 'Clodpole'},
        music: {id: 'music', depth: 0, body: 'Music'},
        cambyses: {id: 'cambyses', depth: 0, body: 'Cambyses'},
        emasculation: {id: 'emasculation', depth: 0, body: 'Emasculation'},
        obtain: {id: 'obtain', depth: 0, body: 'Obtain'},
        tackiness: {id: 'tackiness', depth: 0, body: 'Tackiness'},
        hac: {id: 'hac', depth: 0, body: 'Hac'},
        alternativity: {id: 'alternativity', depth: 0, body: 'Alternativity'},
        campong: {id: 'campong', depth: 0, body: 'Campong'},
        clamorousness: {id: 'clamorousness', depth: 0, body: 'Clamorousness'},
        presubmit: {id: 'presubmit', depth: 0, body: 'Presubmit'},
      },
    }
  },
  computed: {
  },
  methods: {
    notify (event, rowId) {
      console.log(`${event} "${rowId}"`)
      this.$q.notify({message: `${event} "${rowId}"`})
    },
  },
}
</script>
