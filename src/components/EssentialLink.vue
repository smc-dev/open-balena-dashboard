<template>
  <q-item
    clickable
    @click="openRoute"
  >
    <q-item-section
      v-if="icon"
      avatar
    >
      <q-icon :name="icon" />
    </q-item-section>

    <q-item-section>
      <q-item-label>{{ $t(title) }}</q-item-label>
      <q-item-label caption>
        {{ $t(caption) }}
      </q-item-label>
    </q-item-section>
  </q-item>
</template>

<script>
export default {
  name: 'EssentialLink',
  methods: {
    openRoute() {
      if (this.param) {
        this.$router.push({ name: this.link, params: this.param() })
      } else {
        this.$router.push({ name: this.link })
      }
    }

  },
  props: {
    title: {
      type: String,
      required: true
    },

    caption: {
      type: String,
      default: ''
    },

    link: {
      type: String,
      default: '#'
    },
    icon: {
      type: String,
      default: ''
    },
    param: {
      type: Function,
      default: null
    }
  }
}
</script>
