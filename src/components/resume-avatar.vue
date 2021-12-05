<template>
  <div
    @mouseenter="AppMouseOver = true"
    @mouseleave="AppMouseOver = false"
    class="resume-block avatar"
    :class="{'to-delete': AppMouseOverX}"
  >
    <resume-control
      :is-show="AppMouseOver"
      @mouseenter="AppMouseOverX = true"
      @mouseleave="AppMouseOverX = false"
      :id="id"
      @click="$emit('clickX')"
    />
    <img :src="value">
  </div>
</template>

<script>
import ResumeControl from '@/components/resume-control'

export default {
  name: 'resume-avatar',
  emits: ['clickX'],
  props: {
    'value': {
      type: String,
      required: false,
      default: 'https://sun1-83.userapi.com/qjDHi07gAnElE6GlQ7HUeUUuBz0FDjQyBF1ajA/Rp3ExQUgQz0.jpg'
    },
    'id': {
      type: String,
      required: true
    }
  },
  data () {
    return {
      AppMouseOver: false,
      AppMouseOverX: false
    }
  },
  components: { ResumeControl }
}
</script>

<style scoped>

</style>
