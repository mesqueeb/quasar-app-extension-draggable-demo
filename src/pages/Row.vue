<template>
  <div>
    <template v-if="settings.content === 'simple'">
      <div
        class="_row-component"
      >
        {{ body }}
      </div>
    </template>
    <template v-else>
      <q-item
        clickable
        v-ripple
      >
        <q-item-section>
          {{ body }}
        </q-item-section>
        <q-item-section avatar>
          <q-avatar color="primary" text-color="white">
            {{ id.slice(0, 1) }}
          </q-avatar>
        </q-item-section>
      </q-item>
    </template>
  </div>
</template>

<style lang="stylus">

._row-component
  border-bottom solid thin lightgray
  color black
  padding 0.5rem

</style>

<script>
export default {
  name: 'Row',
  props: {
    body: String,
    id: String,
    settings: Object,
  },
  computed: {
  },
  methods: {
  },
}
</script>
