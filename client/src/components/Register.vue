<template>
  <div>
    <h1>Register</h1>
    <input
      type="text"
      name="email"
      placeholder="Email"
      v-model="email"
    />
    <br />
    <input
      type="password"
      name="password"
      placeholder="Password"
      v-model="password"
    />
    <br />
    <button @click="register">
      Register
    </button>
  </div>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'

export default {
  data () {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    async register () {
      try {
        const response = await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
        // Fixed "console.localStorage" (not valid)
        console.log(response.data)
        localStorage.setItem('user', JSON.stringify(response.data))
      } catch (err) {
        console.error(err)
      }
    }
  }
}
</script>

<style scoped>
/* Add styles here */
</style>
