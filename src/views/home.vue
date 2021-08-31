<template>
  <div class="btn" @click="login">google 登入</div>
</template>

<script>
export default {
  setup () {
    const login = () => {
      window.location = `https://accounts.google.com/o/oauth2/v2/auth?redirect_uri=${process.env.VUE_APP_REDIRECT_RUL}/callback&scope=openid email profile https://www.googleapis.com/auth/userinfo.profile https://www.googleapis.com/auth/userinfo.email&response_type=token&client_id=${process.env.VUE_APP_CLIENT_ID}`
    }
    return {
      login
    }
  }
}
</script>

<style lang="scss" scoped>
</style>