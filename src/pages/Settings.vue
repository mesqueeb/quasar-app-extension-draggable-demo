<template>
  <div>
    <q-expansion-item
      expand-separator
    >
      <template v-slot:header>
        <h6 class="q-my-sm q-mr-auto">Settings</h6>
      </template>
      <div class="q-pa-sm">
        <div class="sub-title">Row content</div>
        <div class="q-gutter-sm">
          <q-radio v-model="settings.content" val="simple" label="Simple content" />
          <q-radio v-model="settings.content" val="qitem" label="QItem" />
          <q-radio v-model="settings.content" val="debug" label="Debug" />
        </div>
      </div>
    </q-expansion-item>
  </div>
</template>

<style lang="stylus">

.sub-title
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
  },
}
</script>
