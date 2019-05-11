<template>
<q-markup-table flat>
  <thead>
    <tr>
      <th class="text-left">Action</th>
      <th class="text-left">Touch <q-icon name="touch_app" size="24px" /></th>
      <th class="text-left">Keyboard <q-icon name="keyboard" size="24px" /></th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="row in controlsShown" :key="row.action" class="_tr">
      <td class="text-left" v-html="row.action"></td>
      <td class="text-left">{{ row.touch }}</td>
      <td class="text-left">{{ row.keyboard }}</td>
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
      const mac = this.$q.platform.is.mac
      const option = mac ? 'option' : 'alt'
      const holdToSelect = this.settings.selectionBehaviour === 'hold'
      const controls = [
        {
          action: 'select a row',
          touch: holdToSelect ? 'hold 0.2 sec' : 'tap',
          keyboard: holdToSelect ? 'hold 0.2 sec' : 'click',
        },
        {
          action: `move row up / down\n<sub>(requires selection)</sub>`,
          touch: `drag`,
          keyboard: `${option} up | down`,
        },
        {
          action: `indent / unindent\n<sub>(requires selection)</sub>`,
          touch: `swipe right | left`,
          keyboard: `${option} right | left\ntab | shift tab`,
        },
        {
          action: `select next/previous\n<sub>(requires selection)</sub>`,
          touch: ``,
          keyboard: `up | down`,
        },
        {
          action: 'unselect',
          touch: `tap on selected item\nor outside the rows`,
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
