<template>
  <div class="content" v-on:click="send()">
    <div class="welcome" v-bind:class="colorRound"></div>
    <div class="card login">
      <input type="text" class="input" placeholder="имя" v-model="login" v-bind:class="{ 'error': loginInvalid }">
      <input type="password" class="input" placeholder="пароль" v-model="password" v-bind:class="{ 'error': passwordInvalid }">
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Login',
  data: function () {
    return {
      login: '',
      password: '',
      loginInvalid: false,
      passwordInvalid: false,
      colorRound: '',
      status: 500
    }
  },
  methods: {
    send: function () {
      this.login === '' ? this.loginInvalid = true : this.loginInvalid = false
      this.password === '' ? this.passwordInvalid = true : this.passwordInvalid = false
      if (this.login !== '' && this.password !== '') {
        this.colorRound = 'grayRound'
        this.status = 200
        axios
          .get('https://api.coindesk.com/v1/bpi/currentprice.json')
          .then(response => (this.status = response.status))
        console.log(this.status)
        if (this.status === 200) {
          this.colorRound = 'greenRound'
          this.$router.push('grid')
        } else {
          this.colorRound = 'redRound'
        }
      }
    }
  }
}
</script>

<style scoped>

.login{
  padding: 40px;
  width: 30%;
  min-width: 250px;
}

.input{
  display: block;
  padding: 20px;
  margin-bottom: 40px;
  font-size: 25px;
  border-radius: 10px;
  border: 2px solid gray;
  transition: 0.2s;
  width: 100%;
}

.input:focus{
  border: 2px solid var(--violet);
}

.welcome{
  width: 55px;
  height: 55px;
  margin: 25px;
  border: 10px solid var(--violet);
  border-radius: 50px;
  background-color: var(--violet);
  opacity: 0.5;
  transition: 0.2s;
}

.welcome:hover{
  width: 0px;
  height: 0px;
  border: 37.5px solid white;
  opacity: 1.0;
}

.error{
  border: 2px solid red;
}

.redRound{
  border-color: red;
  background-color: red;
  opacity: 1.0;
}

.greenRound{
  border-color: green;
  background-color: green;
  opacity: 1.0;
}

.grayRound{
  border-color: gray;
  background-color: gray;
  opacity: 0.5;
}

</style>
