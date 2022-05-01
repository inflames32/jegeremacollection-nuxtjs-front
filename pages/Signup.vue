<template>
  <div class="signup">
    <NuxtLink class="btn-back" to="/"> Back </NuxtLink>
    <div class="form">
      <form class="form-signup">
        <input
          type="email"
          placeholder="Email"
          v-model="email"
          required
          class="input email"
        />
        <input
          type="password"
          placeholder="Mot de passe"
          v-model="password"
          required
          class="input password"
        />
        <input
          type="password"
          placeholder="Confimer le mot de passe"
          v-model="password_validation"
          required
          class="input password"
        />
        <button type="submit" class="button btn-submit" @click="submitSignup">
          Créer
        </button>
      </form>
      <div class="message" v-show="message !== ''">{{ this.message }}</div>
    </div>
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
  methods: {
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
  },
}
</script>

<style lang="scss">
.signup {
  width: 100%;
  height: calc(100vh - 80px);
}
.form {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  &-signup {
    display: flex;
    flex-direction: column;
  }
}
.form-signup {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
}
.input {
  width: 400px;
  height: 40px;
  padding: 5px 10px;
  margin: 15px 0 15px 0;
}
.btn-submit {
  text-align: center;
  font-size: 16px;
  font-weight: bold;
  line-height: 30px;
  color: white;
  background-color: green;
  border: none;
  border-radius: 4px;
  text-decoration: none;
  padding: 6px 14px;
}
.btn-submit:hover {
  background-color: rgb(16, 70, 16);
  transition: 0.5s;
}
.message {
  margin-top: 50px;
  color: white;
  cursor: pointer;
  font-size: 20px;
  text-decoration: none;
}
</style>