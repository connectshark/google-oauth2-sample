<template>
  <h2>welcome back</h2>
  <div class="img-place" v-if="img">
    <img :src="img" :alt="name">
  </div>
  <p>{{name}}</p>
  <p>{{email}}</p>
</template>

<script>
import axios from 'axios'
import { ref } from 'vue'
import { useRoute } from 'vue-router'
export default {
  setup () {
    const email = ref('')
    const img = ref('')
    const name = ref('')
    const route = useRoute()
    axios({
      baseURL: process.env.VUE_APP_API_URL,
      url: '/google/login',
      params: {
        code: route.query.code
      }
    }).then(res => {
      img.value = res.data.picture
      email.value = res.data.email
      name.value = res.data.name
    })
    return {
      email,
      img,
      name
    }
  }
}
</script>

<style lang="scss" scoped>
img{
  vertical-align: middle;
  width: 100%;
}
.img-place{
  width: 80px;
}
</style>