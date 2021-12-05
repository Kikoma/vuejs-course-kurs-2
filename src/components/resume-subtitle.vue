<template>
  <div
    @mouseenter="AppMouseOver = true"
    @mouseleave="AppMouseOver = false"
    class="resume-block"
    :class="{'to-delete': AppMouseOverX}"
  >
    <resume-control
      :is-show="AppMouseOver"
      @mouseenter="AppMouseOverX = true"
      @mouseleave="AppMouseOverX = false"
      :id="id"
      @click="$emit('clickX')"
    />
    <h2>{{ value }}</h2>
  </div>
</template>

<script>
import ResumeControl from '@/components/resume-control'

export default {
  name: 'resume-subtitle',
  props: {
    'value': String,
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
