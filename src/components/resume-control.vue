<template>
  <div
    class="delete-block" :class="{w100: MouseOnX}"
    v-show="isShow"
    @mouseenter="MouseOnX = true"
    @mouseleave="MouseOnX = false"
  >
    X Удалить
  </div>
</template>

<script>
export default {
  name: 'resume-control',
  props: {
    'isShow': {
      type: Boolean,
      required: false,
      default: false
    },
    id: {
      type: String,
      required: true
    }
  },
  data () {
    return {
      MouseOnX: false
    }
  }
}
</script>

<style scoped>

</style>
