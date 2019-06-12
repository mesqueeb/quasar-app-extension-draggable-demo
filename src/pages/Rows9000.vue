<template>
<div>
  <div class="text-negative q-my-sm">
    It gets slow around 200+ rows. I'm still working on improving the performance.
  </div>
  <q-draggable-rows
    v-model="rowOrder"
    ref="rowsRef"
  >
    <q-draggable-row
      v-for="rowId in rowOrder"
      :id="rowId"
      v-model="rows[rowId].depth"
      :collapsed.sync="rows[rowId].collapsed"
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
      <template
        v-slot:selection-indicator
        v-if="settings.selectionIndicator === 'qcard'"
      >
        <q-card />
      </template>
    </q-draggable-row>
  </q-draggable-rows>
</div>
</template>

<style lang="stylus">
</style>

<script>
import Row from './Row'

function createBatcher (
  handler,
  max = 100,
){
  let hasJobs = false
  const queue = []

  return {
    changeHandler (fn) {
      handler = fn
    },
    queue(items) {
      queue.push(...items)
      if(!hasJobs) {
        hasJobs = true
        doBatch()
      }
    },
    cancel (purgeQueue = true) {
      hasJobs = false
      if(purgeQueue) queue.splice(0)
    }
  }

  function doBatch () {
    if (!hasJobs) return
    const batch = queue.splice(0,max)
    handler(batch)

    if(!queue.length) hasJobs = false
    if(hasJobs) requestAnimationFrame(doBatch)
  }
}

export default {
  name: 'Rows',
  components: { Row },
  props: {
    settings: Object,
  },
  created () { this.load() },
  mounted () { this.settings.rowsRef = this.$refs.rowsRef },
  data () {
    const rowOrderSection = [
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
    ]
    let rowIdsToAdd = [
      'all',
    ]
    let i = 10
    while (i > 0) {
      rowIdsToAdd = rowIdsToAdd.concat(rowOrderSection.map(id => id + i))
      i--
    }
    const rows = {
      all: {id: 'all', depth: 0, body: 'All', collapsed: true},
      overacceleration: {id: 'overacceleration', depth: 1, body: 'Overacceleration'},
      crunchable: {id: 'crunchable', depth: 1, body: 'Crunchable', collapsed: true},
      increasedly: {id: 'increasedly', depth: 2, body: 'Increasedly'},
      nova: {id: 'nova', depth: 3, body: 'Nova'},
      oracles: {id: 'oracles', depth: 2, body: 'Oracles'},
      introject: {id: 'introject', depth: 1, body: 'Introject'},
      dibai: {id: 'dibai', depth: 1, body: 'Dibai'},
      pashim: {id: 'pashim', depth: 1, body: 'Pashim'},
      swelteringly: {id: 'swelteringly', depth: 1, body: 'Swelteringly'},
      elaborating: {id: 'elaborating', depth: 1, body: 'Elaborating'},
      middle: {id: 'middle', depth: 1, body: 'Middle'},
      muff: {id: 'muff', depth: 1, body: 'Muff'},
      prewelcome: {id: 'prewelcome', depth: 1, body: 'Prewelcome'},
      unvivid: {id: 'unvivid', depth: 1, body: 'Unvivid'},
      suttner: {id: 'suttner', depth: 1, body: 'Suttner'},
      stilton: {id: 'stilton', depth: 1, body: 'Stilton'},
      beret: {id: 'beret', depth: 1, body: 'Beret'},
      faller: {id: 'faller', depth: 1, body: 'Faller'},
      clodpole: {id: 'clodpole', depth: 1, body: 'Clodpole'},
      music: {id: 'music', depth: 1, body: 'Music'},
      cambyses: {id: 'cambyses', depth: 1, body: 'Cambyses'},
      emasculation: {id: 'emasculation', depth: 1, body: 'Emasculation'},
      obtain: {id: 'obtain', depth: 1, body: 'Obtain'},
      tackiness: {id: 'tackiness', depth: 1, body: 'Tackiness'},
      hac: {id: 'hac', depth: 1, body: 'Hac'},
      alternativity: {id: 'alternativity', depth: 1, body: 'Alternativity'},
      campong: {id: 'campong', depth: 1, body: 'Campong'},
      clamorousness: {id: 'clamorousness', depth: 1, body: 'Clamorousness'},
      presubmit: {id: 'presubmit', depth: 1, body: 'Presubmit'},
    }
    rowIdsToAdd.forEach(id => {
      if (rows[id]) return
      rows[id] = {id, depth: 1, body: id.toUpperCase()}
    })
    return {
      rowIdsToAdd,
      rowOrder: [],
      rows
    }
  },
  computed: {
  },
  methods: {
    notify (event, rowId) {
      console.log(`${event} "${rowId}"`)
      this.$q.notify({message: `${event} "${rowId}"`})
    },
    load () {
      const ro = this.rowOrder
      const rafBatch = createBatcher(ids => ro.push(...ids), 500)
      rafBatch.queue(this.rowIdsToAdd)
    }
  },
}
</script>
