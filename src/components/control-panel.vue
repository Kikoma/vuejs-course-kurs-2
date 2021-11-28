<template>
  <form class="card card-w30">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" :rows="rows" v-model="value"></textarea>
    </div>

    <button
      type="button"
      class="btn primary"
      :disabled="value.length <= 3"
      @click="btnAddClick"
    >Добавить
    </button>
  </form>
</template>

<script>
export default {
  emits: ['addBlock'],
  data () {
    return {
      type: '',
      value: '',
      rows: 3
    }
  },
  methods: {
    btnAddClick () {
      this.$emit('addBlock', this.type, this.value)
      this.initForm()
    },
    initForm () {
      this.type = 'title'
      this.value = ''
    }
  },
  mounted () {
    this.initForm()
  }
}
</script>

<style scoped>

</style>
