<template>
  <div>
    <h6 class="q-my-sm q-mx-md">Demo</h6>
    <q-draggable-rows
      v-model="rowsOrder"
      :depthMap="rowsDepthMap"
    >
      <q-draggable-row
        v-for="rowId in rowsOrder"
        :id="rowId"
        v-model="rows[rowId].depth"
        @click.native="notify('tapped', rowId)"
        @held="notify('held', rowId)"
        :hold-to-select="false"
        :key="`row-${rowId}`"
        class="_row"
      >
        <Row
          :body="rows[rowId].body"
          :id="rowId"
          :settings="settings"
        />
        <!-- <template v-slot:selection-indicator>
          <div class="_selection-indicator"></div>
        </template> -->
      </q-draggable-row>
    </q-draggable-rows>
  </div>
</template>

<style lang="stylus">

._row
  padding 0
  border none
  background transparent

</style>

<script>
import Row from './Row'
export default {
  name: 'Rows',
  components: { Row },
  props: {
    settings: Object,
  },
  data () {
    return {
      rowsOrder: [
        'clodpole',
        'increasedly',
        'dibai',
        'pashim',
        'swelteringly',
        'introject',
        'elaborating',
        'middle',
        'muff',
        'prewelcome',
        'unvivid',
        'suttner',
        'stilton',
        'beret',
        'faller',
        'overacceleration',
        'music',
        'cambyses',
        'emasculation',
        'obtain',
        'crunchable',
        'tackiness',
        'hac',
        'alternativity',
        'campong',
        'oracles',
        'clamorousness',
        'presubmit',
        'nova',
      ],
      rows: {
        clodpole: {id: 'clodpole', depth: 0, body: 'Clodpole'},
        increasedly: {id: 'increasedly', depth: 0, body: 'Increasedly'},
        dibai: {id: 'dibai', depth: 0, body: 'Dibai'},
        pashim: {id: 'pashim', depth: 0, body: 'Pashim'},
        swelteringly: {id: 'swelteringly', depth: 0, body: 'Swelteringly'},
        introject: {id: 'introject', depth: 0, body: 'Introject'},
        elaborating: {id: 'elaborating', depth: 0, body: 'Elaborating'},
        middle: {id: 'middle', depth: 0, body: 'Middle'},
        muff: {id: 'muff', depth: 0, body: 'Muff'},
        prewelcome: {id: 'prewelcome', depth: 0, body: 'Prewelcome'},
        unvivid: {id: 'unvivid', depth: 0, body: 'Unvivid'},
        suttner: {id: 'suttner', depth: 0, body: 'Suttner'},
        stilton: {id: 'stilton', depth: 0, body: 'Stilton'},
        beret: {id: 'beret', depth: 0, body: 'Beret'},
        faller: {id: 'faller', depth: 0, body: 'Faller'},
        overacceleration: {id: 'overacceleration', depth: 0, body: 'Overacceleration'},
        music: {id: 'music', depth: 0, body: 'Music'},
        cambyses: {id: 'cambyses', depth: 0, body: 'Cambyses'},
        emasculation: {id: 'emasculation', depth: 0, body: 'Emasculation'},
        obtain: {id: 'obtain', depth: 0, body: 'Obtain'},
        crunchable: {id: 'crunchable', depth: 0, body: 'Crunchable'},
        tackiness: {id: 'tackiness', depth: 0, body: 'Tackiness'},
        hac: {id: 'hac', depth: 0, body: 'Hac'},
        alternativity: {id: 'alternativity', depth: 0, body: 'Alternativity'},
        campong: {id: 'campong', depth: 0, body: 'Campong'},
        oracles: {id: 'oracles', depth: 0, body: 'Oracles'},
        clamorousness: {id: 'clamorousness', depth: 0, body: 'Clamorousness'},
        presubmit: {id: 'presubmit', depth: 0, body: 'Presubmit'},
        nova: {id: 'nova', depth: 0, body: 'Nova'},
      },
    }
  },
  computed: {
    rowsDepthMap () {
      return Object.values(this.rows)
        .reduce((carry, row) => {
          carry[row.id] = row.depth
          return carry
        }, {})
    },
  },
  methods: {
    notify (event, rowId) {
      console.log(`${event} "${rowId}"`)
      this.$q.notify({message: `${event} "${rowId}"`})
    },
  },
}
</script>
