<template>
  <div>
    <h1>Signup</h1>
    <div>S'inscrire</div>
    <NuxtLink class="btn-back" to="/"> Back </NuxtLink>
    <form>
      <input type="text" placeholder="Email" v-model="email" required />
      <input
        type="password"
        placeholder="Mot de passe"
        v-model="password"
        required
      /><input
        type="password"
        placeholder="Confimer le mot de passe"
        v-model="password_validation"
        required
      />
      <button type="submit" class="button btn-submit" @click="submitSignup">
        Créer
      </button>
    </form>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'signup',
  data() {
    return {
      email: '',
      password: '',
      password_validation: '',
    }
  },
  async submitSignup(e) {
    e.preventDefault()
    const signupSubmit = axios.post(`http://localhost:5000/signup`, {
      email: this.email,
      password: this.password,
      password_validation: this.password_validation,
    })
    const result = await signupSubmit
    console.log(result)
    const message = result.data.message
    console.log(message)
  },
}
</script>