<template>
  <h2>welcome back</h2>
  <p>{{email}}</p>
</template>

<script>
import axios from 'axios'
import { ref } from 'vue'
import { useRoute } from 'vue-router'
export default {
  setup () {
    const email = ref('')
    const route = useRoute()
    axios({
      baseURL: process.env.VUE_APP_API_URL,
      url: '/google/login',
      params: {
        code: route.query.code
      }
    }).then(res => {
      console.log(res.data)
    })
    return {
      email
    }
  }
}
</script>

<style lang="scss" scoped>
</style>