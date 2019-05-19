<template>
<q-markup-table flat>
  <thead>
    <tr>
      <th class="text-left"></th>
      <th class="text-left">Touch <q-icon name="touch_app" size="24px" /></th>
      <th class="text-left">Keyboard <q-icon name="keyboard" size="24px" /></th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="row in controlsShown" :key="row.action" class="_tr">
      <td class="text-left" v-html="row.action"></td>
      <td class="text-left" v-html="row.touch"></td>
      <td class="text-left" v-html="row.keyboard"></td>
    </tr>
    <tr>
      <td
        @click="showMore = !showMore"
        class="text-left text-primary cursor-pointer"
        colspan="3"
      >Show {{ showMore ? 'less' : 'more' }}</td>
    </tr>
  </tbody>
</q-markup-table>
</template>

<style lang="stylus">

._tr > td
  white-space pre-line
  sub
    color gray

</style>

<script>
export default {
  name: 'Controls',
  props: {
    settings: Object,
  },
  data () {
    return {
      showMore: false,
    }
  },
  computed: {
    controls () {
      const requestFeature = `<sub>not yet implemented\n<a href="https://github.com/mesqueeb/quasar-app-extension-draggable/issues">request</a></sub>`
      const selectionReq = `\n<sub>(requires selection)</sub>`
      const mac = this.$q.platform.is.mac
      const option = mac ? 'option' : 'alt'
      const cmd = mac ? 'command' : 'windows-key'
      const holdToSelect = this.settings.selectionBehaviour === 'hold'
      const controls = [
        {
          action: 'select a row',
          touch: holdToSelect ? 'hold 0.2 sec' : 'tap',
          keyboard: holdToSelect ? 'hold 0.2 sec' : 'click',
        },
        {
          action: `move row up / down${selectionReq}`,
          touch: `drag`,
          keyboard: `${option} up | down`,
        },
        {
          action: `indent / unindent${selectionReq}`,
          touch: `swipe right | left`,
          keyboard: `${option} right | left\ntab | shift tab`,
        },
        {
          action: `select next/previous${selectionReq}`,
          touch: ``,
          keyboard: `up | down`,
        },
        {
          action: `hide/show sub-rows${selectionReq}`,
          touch: `tap the arrow icon`,
          keyboard: `left | right`,
        },
        {
          action: 'select multiple rows',
          touch: requestFeature,
          keyboard: `hold ${cmd} + click\nhold shift + click`,
        },
        {
          action: 'unselect all',
          touch: `tap outside the rows`,
          keyboard: `esc`,
        },
      ]
      return controls
    },
    controlsShown () {
      return this.showMore ? this.controls : this.controls.slice(0, 3)
    },
  },
}
</script>
