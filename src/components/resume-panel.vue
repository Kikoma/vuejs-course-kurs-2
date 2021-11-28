<template>
  <div class="card card-w70" v-if="resume.length">
    <div
      v-for="resBlock in resume"
      :key="resBlock.id"
    >
      <component
        :is="'resume-'+ resBlock.type"
        :value="resBlock.value"
      ></component>
    </div>
  </div>
  <div class="card card-w70" v-else>
    <h3>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import ResumeTitle from '@/components/resume-title'
import ResumeAvatar from '@/components/resume-avatar'
import ResumeSubtitle from '@/components/resume-subtitle'
import ResumeText from '@/components/resume-text'

export default {
  name: 'resume-panel',
  data() {
    return {
      activeBlock : ""
    }
  },
  props: {
    'resume' : {
      type: Array,
      require: true
    }
  },
  components: {
    ResumeText,
    ResumeSubtitle,
    ResumeTitle,
    ResumeAvatar
  }
}
</script>

<style scoped>

</style>
