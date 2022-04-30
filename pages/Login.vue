<template>
  <div>
    <h1>Login</h1>
    <div>Se connecter</div>

    <NuxtLink class="btn-back" to="/"> Back </NuxtLink>
    <form>
      <input type="text" placeholder="Email" v-model="email" required />
      <input
        type="password"
        placeholder="Mot de passe"
        v-model="password"
        required
      />
      <button type="submit" class="button btn-submit" @click="submitLogin">
        Connexion
      </button>
      <NuxtLink class="btn-signup" to="/signup"> Pas de compte? </NuxtLink>
    </form>
    <div v-show="message !== ''">{{ this.message }}</div>
  </div>
</template>


<script>
import axios from 'axios'
export default {
  name: 'login',
  data() {
    return {
      email: '',
      password: '',
      error: '',
      message: '',
    }
  },
  methods: {
    async submitLogin(e) {
      e.preventDefault()
      const dataSubmit = axios.post(`http://localhost:5000/login`, {
        email: this.email,
        password: this.password,
      })

      const result = await dataSubmit
      console.log(result)
      const message = result.data.message
      console.log(message)

      /* try {
        console.log('ici login')
        await this.$axios.post(`http://localhost:5000/login`, {})
      } catch (e) {
        console.log(e)
        this.error = e.response.data.message
      } */
    },
  },
}
</script>