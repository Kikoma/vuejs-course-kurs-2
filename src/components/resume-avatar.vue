<template>
  <div class="avatar">
    <img :src="value">
  </div>
</template>

<script>
export default {
  name: 'resume-avatar',
  props: {
    'value': {
      type: String,
      required: false,
      default: 'https://sun1-83.userapi.com/qjDHi07gAnElE6GlQ7HUeUUuBz0FDjQyBF1ajA/Rp3ExQUgQz0.jpg'
    }
  }
}
</script>

<style scoped>

</style>
