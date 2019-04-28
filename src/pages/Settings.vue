<template>
  <div>
    <div class="sub-title">Row content</div>
    <!-- <div v-for="option in options" :key=""> -->
    <div class="q-gutter-sm">
      <q-radio
        v-model="settings.content"
        val="simple"
        label="Simple content"
        @input="unselectRow"
      />
      <q-radio
        v-model="settings.content"
        val="qitem"
        label="Use QItem as row"
        @input="unselectRow"
      />
      <!-- <q-radio v-model="settings.content" val="debug" label="Debug" /> -->
    </div>
    <div class="sub-title">Selection indicator</div>
    <div class="q-gutter-sm">
      <q-radio
        v-model="settings.selectionIndicator"
        val="default"
        label="Default"
      />
      <q-radio
        v-model="settings.selectionIndicator"
        val="qcard"
        label="Use QCard as selection indicator"
      />
    </div>

    <div class="sub-title">Selection behaviour</div>
    <div class="q-gutter-sm">
      <q-radio
        v-model="settings.selectionBehaviour"
        val="default"
        label="Click to select (default)"
      />
      <q-radio
        v-model="settings.selectionBehaviour"
        val="hold"
        label="Hold to select"
      />
    </div>
  </div>
</template>

<style lang="stylus">

.sub-title
  margin-top 0.5em
  padding 0 .5em
  font-weight 400

</style>

<script>
export default {
  name: 'PageIndex',
  props: {
    settings: Object,
  },
  computed: {
  },
  methods: {
    unselectRow () {
      this.settings.rowsRef.selectId(null)
    },
  },
}
</script>
