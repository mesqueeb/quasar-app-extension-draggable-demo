<template>
  <div>
    <template v-if="settings.content === 'simple'">
      <div
        class="_row-component"
      >
        <div>{{ body }}</div>
        <q-draggable-row-collapse-arrow />
      </div>
    </template>
    <template v-if="settings.content === 'qitem'">
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
        <q-item-section side>
          <q-draggable-row-collapse-arrow />
        </q-item-section>
      </q-item>
    </template>
    <!-- <template v-if="settings.content === 'debug'">
      <div
        class="_row-component --debug"
      >
        <div>{{ body }}</div>
        <div class="_row-dimensions">
          <div><span class="text-gray">top:</span> {{ elOffsetTop }}</div>
          <div><span class="text-gray">height:</span> {{ elHeight }}</div>
          <div>{{ selected ? 'selected' : '' }}</div>
        </div>
      </div>
    </template> -->
  </div>
</template>

<style lang="stylus">

._row-component
  border-bottom solid thin lightgray
  color black
  position relative
  display flex
  > *:first-child
    padding 0.5rem
    flex 1
  &.--debug
    min-height 100px
    border-top 10px solid lightgray
    border-right 10px solid $primary
    border-bottom 10px solid $secondary
    border-left 10px solid $accent
._row-dimensions
  position absolute
  top 0
  bottom 0
  left 0
  right 0
  display flex
  justify-content space-between
  align-items center
  flex-direction column

</style>

<script>
export default {
  name: 'Row',
  props: {
    body: String,
    id: String,
    settings: Object,
    selected: Boolean,
    elOffsetTop: Number,
    elHeight: Number,
  },
  computed: {
  },
  methods: {
  },
}
</script>
