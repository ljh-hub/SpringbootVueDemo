<template xmlns:v-on="http://www.w3.org/1999/xhtml">
    <div>
      <p>login .vue</p>
        用户名:<input type="text" v-model="loginForm.username" placeholder="请输入用户名"/>
        <br><br>
        密码： <input type="password" v-model="loginForm.password" placeholder="请输入密码"/>
        <br><br>
        <button v-on:click="login">登录</button>
    </div>
</template>

<script>
export default {
  name: 'Login.vue',
  data () {
    return {
      loginForm: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    login () {
      // alert('用户名' + this.data.username + '密码' + this.data.password)
      alert('用户名' + this.loginForm.username + '密码' + this.loginForm.password)
      this.$axios
        .post('/login', {
          username: this.loginForm.username,
          password: this.loginForm.password
        })
        .then(successResponse => {
          if (successResponse.data.code === 200) {
            this.$router.replace({path: '/index'})
          }
        })
        .catch(failResponse => {
        })
    }
  }
}
</script>

<style scoped>

</style>
