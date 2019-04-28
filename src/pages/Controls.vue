<template>
<q-markup-table flat>
  <thead>
    <tr>
      <th class="text-left">Action</th>
      <th class="text-left">Hotkeys</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="row in controlsShown" :key="row.action" class="_tr">
      <td class="text-left">{{ row.action }}</td>
      <td class="text-left">{{ row.key }}</td>
    </tr>
    <tr>
      <td
        @click="showMore = !showMore"
        class="text-left text-primary cursor-pointer"
        colspan="2"
      >Show {{ showMore ? 'less' : 'more' }}</td>
    </tr>
  </tbody>
</q-markup-table>
</template>

<style lang="stylus">

._tr > td
  white-space pre-line

</style>

<script>
export default {
  name: 'Controls',
  data () {
    const mac = this.$q.platform.is.mac
    return {
      showMore: false,
      controls: [
        {
          action: 'select a row',
          key: 'click\nclick and hold (depending on settings)',
        },
        {
          action: 'select next/previous',
          key: `up/down`,
        },
        {
          action: 'move row up/down',
          key: `drag\n${ mac ? 'option' : 'alt' } + up/down`,
        },
        {
          action: 'indent\nunindent',
          key: `tab\nshift + tab`,
        },
        {
          action: 'unselect',
          key: `esc\nclick on selected item`,
        },
      ]
    }
  },
  computed: {
    controlsShown () {
      return this.showMore ? this.controls : this.controls.slice(0, 3)
    },
  },
  methods: {
  },
}
</script>
