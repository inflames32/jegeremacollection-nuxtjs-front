<template>
  <div class="login">
    <NuxtLink class="btn-back" to="/"> Back </NuxtLink>
    <div class="form">
      <form class="form-login">
        <input
          type="text"
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
        <button type="submit" class="button btn-submit" @click="submitLogin">
          Connexion
        </button>
        <div class="message" v-show="message !== ''">{{ this.message }}</div>
        <NuxtLink class="link-signup" to="/signup"> Pas de compte? </NuxtLink>
      </form>
    </div>
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
      logged: '',
      user: {},
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
      this.message = result.data.message
      this.logged = result.data.logged
      console.log('this.message', this.message)
      console.log('this.logged', this.logged)
    },
  },
}
</script>

<style lang="scss">
.login {
  width: 100%;
  height: calc(100vh - 80px);
}
.form {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  &-login {
    display: flex;
    flex-direction: column;
  }
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
.link-signup {
  margin-top: 50px;
  color: white;
  cursor: pointer;
  font-size: 20px;
  text-decoration: none;
}
.link-signup:hover {
  transition: 0.3s;

  color: rgb(180, 166, 166);
}
.message {
  margin-top: 50px;
  color: white;
  cursor: pointer;
  font-size: 20px;
  text-decoration: none;
}
.btn-back {
  margin-left: 32px;
  align-self: flex-start;
  margin-bottom: 32px;
  text-align: center;
  font-size: 16px;
  font-weight: bold;
  line-height: 30px;
  color: white;
  background-color: red;
  border: none;
  border-radius: 4px;
  text-decoration: none;
  padding: 6px 14px;
}
.btn-back:hover {
  background-color: rgb(138, 36, 36);
  transition: 0.3s;
}
.input:hover {
  border: 2px solid blue;
}
</style>