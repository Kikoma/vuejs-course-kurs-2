<template>
  <div class="container">
    <p>
      <button class="btn primary" @click="$emit('loadComments')">{{ !comments.length ? 'Загрузить': 'Обновить' }}  комментарии</button>
    </p>
    <div class="card">
      <h2>Комментарии</h2>
      <AppLoaderbgWhite v-if="ShowLoader"/>
      <ul class="list" v-if="comments.length">
        <li class="list-item"
            v-for="comment in comments"
            :key="comment.id"
        >
          <div>
            <p><strong>{{ comment.email }}</strong></p>
            <small>{{ comment.body }}</small>
          </div>
        </li>
      </ul>
      <p v-else> Комментариев пока нет или не загружены</p>
    </div>
  </div>
</template>

<script>
import AppLoaderbgWhite from '@/components/AppLoaderbgWhite'
export default {
  name: 'comments-panel',
  emits: ['loadComments'],
  props: {
    'ShowLoader': {
      type: Boolean,
      required: false,
      default: false
    },
    'comments': {
      type: Object,
      default: function() {
        return {
          id: -1,
          email: 'smbd@example.com',
          body: 'lorem'
        }
      }
    }
  },
  components: {AppLoaderbgWhite}
}
</script>

<style scoped>

</style>
