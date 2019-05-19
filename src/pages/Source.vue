<template>
  <div class="q-pa-sm">
    The source code below is generated based on the options you picked in the "settings" tab.
    <div class="flex q-gutter-sm">
      <div class="_code-section">
        <h6 class="q-mt-none q-mb-sm">Script</h6>
        <q-input
          autogrow
          standout
          v-model="sourceCodeScript"
          type="textarea"
          input-class="code-font"
        />
      </div>
      <div class="_code-section">
        <h6 class="q-mt-none q-mb-sm">Template</h6>
        <q-input
          autogrow
          standout
          v-model="sourceCodeTemplate"
          type="textarea"
          input-class="code-font"
        />
      </div>
      <div class="q-mt-md">
        <h6 class="q-mt-none q-mb-sm">Hints</h6>
        It is not required to pass the <code class="_code">collapsed</code> prop. The prop is <code class="_code">false</code> by default.
      </div>
    </div>
  </div>
</template>

<style lang="stylus">

._code-section
  min-width 400px
._code
  background rgba(0,0,0,.05)
  padding 0 .4em
  border-radius .2em

</style>

<script>
export default {
  name: 'Source',
  props: {
    settings: Object,
  },
  data () {
    return {}
  },
  computed: {
    sourceCodeTemplate () {
      const s = this.settings

      const rowContent = (s.content === 'simple')
        ? `
    <div>
      {{ rows[id].body }}
      <q-draggable-row-collapse-arrow />
    </div>`
        : `
    <q-item clickable v-ripple>
      <q-item-section>
        {{ rows[id].body }}
      </q-item-section>
      <q-item-section side>
        <q-draggable-row-collapse-arrow />
      </q-item-section>
    </q-item>`

      const holdToSelect = (s.selectionBehaviour !== 'hold')
        ? ''
        : `
    :hold-to-select="true"`

      const selectionIndicator = (s.selectionIndicator === 'default')
        ? ''
        : `
    <template v-slot:selection-indicator>
      <q-card />
    </template>`

      const all = `<q-draggable-rows
  v-model="order"
>
  <q-draggable-row
    v-for="id in order"
    :key="id"
    :id="id"
    v-model="rows[id].depth"${holdToSelect}
    :collapsed.sync="rows[id].collapsed"
  >${rowContent}${selectionIndicator}
  </q-draggable-row>
</q-draggable-rows>`

      return all
    },
    sourceCodeScript () {
      return `const order = [
  id1,
  id2,
  // ...
]
const rows = {
  id1: {depth: 0, body: 'I am row one!'},
  id2: {depth: 0, body: 'Another row bro!', collapsed: true},
  // ...
}
export default {
  data () {
    return { order, rows }
  }
}`
    },
  },
  methods: {
  },
}
</script>
