<template>
  <div class="container column">
    <control-panel @addBlock="AppResumeAddBlock"/>
    <ResumePanel :resume="resume" @clickX="DeleteResumeBlock"/>
  </div>
  <CommentsPanel
    :comments="comments"
    :ShowLoader="loadingComments"
    @loadComments="AppLoadComments"
  />
  <AppLoader v-if="false"/>
</template>

<script>
import ControlPanel from '@/components/control-panel'
import ResumePanel from '@/components/resume-panel'
import CommentsPanel from '@/components/comments-panel'
import AppLoader from '@/components/AppLoader'
import axios from 'axios'

export default {
  data () {
    return {
      loadingComments: false,
      comments: [],
      resume: []
    }
  },
  methods: {
    async AppLoadComments () {
      this.loadingComments = true
      try {
        const { data } = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')
        if (!data) {
          throw new Error('Список комментариев пуст')
        }
        this.comments = data
        this.loadingComments = false
      } catch (e) {
        this.alert = {
          type: 'danger',
          title: 'Ошибка!',
          text: e.message
        }
        this.loadingComments = false
        console.log(e.message)
      }
    },
    async AppResumeAddBlock (type, value) {
      // const response = await fetch('https://vladilen-vue-course-kurs2-default-rtdb.europe-west1.firebasedatabase.app/resume.json',{
      //   method: 'POST',
      //   headers: {
      //     'Content-Type': 'Application/json'
      //   },
      //   body: JSON.stringify({"type": type, "value": value})
      // })
      // const fbData = await response.json()
      // console.log(fbData)

      const { data } = await axios({
        method: 'post',
        url: 'https://vladilen-vue-course-kurs2-default-rtdb.europe-west1.firebasedatabase.app/resume.json',
        headers: {
          'Content-Type': 'Application/json'
        },
        data: {
          'type': type,
          'value': value
        }
      })
      await this.AppGetResume()
    },
    async AppGetResume () {
      const { data } = await axios.get('https://vladilen-vue-course-kurs2-default-rtdb.europe-west1.firebasedatabase.app/resume.json')
      this.resume = Object.keys(data).map(key => {
        return {
          id: key,
          ...data[key]
        }
      })
    },
    DeleteResumeBlock (id) {
      if (confirm('Удалить блок?\nВосстановление будет невозможно!')) {
        // this.AppFBDeleteBlock(id)
         alert('Deleting block with id=' + id + '\nБлок не удален, т.к. функционал не реализован')
      }

    },
    async AppFBDeleteBlock (id) {
      const response = await axios.delete(
        'https://vladilen-vue-course-kurs2-default-rtdb.europe-west1.firebasedatabase.app/resume.json',
        {
          data: { 'id': id }
        }
      )
      console.log('response=', response)
      await this.AppGetResume()
    }
  },
  mounted () {
    this.AppGetResume()
  }
  ,
  components: {
    ControlPanel,
    ResumePanel,
    CommentsPanel,
    AppLoader
  }
}
</script>

<style>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
