<template>
  <div v-html="value"></div>
</template>

<script>
export default {
  name: 'resume-text',
  props: {
    'value': String
  }
}

</script>

<style scoped>

</style>
