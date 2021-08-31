<template>
  <h2>welcome back</h2>
  <p>{{email}}</p>
</template>

<script>
import axios from 'axios'
import { ref } from 'vue'
export default {
  setup () {
    const email = ref('')
    const url =  new URL(location.href.replace('#', '?'))
    const token = url.searchParams.get('access_token')

    axios({
      baseURL: process.env.VUE_APP_API_URL,
      url: '/google/login',
      params: {
        token
      }
    }).then(res => {
      email.value = res.data.email
    })

    return {
      email
    }
  }
}
</script>

<style lang="scss" scoped>
</style>