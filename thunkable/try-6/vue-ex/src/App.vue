<script setup>
import { ref, useTemplateRef } from 'vue'
import Card from './components/Card.vue'

const users = [
  {
    login: 'alex',
    pwd: 'zxc'
  },
  {
    login: 'rain',
    pwd: 'rrr'
  },
]
let loggedInState = ref('not logged in')  // 'login error' | 'logged in'
const login = useTemplateRef('login')
const pwd = useTemplateRef('pwd')

function subm() {
  console.log(login.value.value)
  console.log(pwd.value.value)

  for (const user of users) {
    if (user.login === login.value.value && user.pwd === pwd.value.value) {
      loggedInState.value = 'logged in'
    } else {
      loggedInState.value = 'login error'
    }
  }
}
</script>

<template>
  <main class="cont">
    <form>
      <p>Логин:</p>
      <input ref="login">
      <p>Пароль:</p>
      <input ref="pwd" type="password">
      <br>
      <br>
      <button @click="subm" type="submit">Войти ({{ loggedInState }})</button>
    </form>

    <p style="color: green;" v-if="loggedInState === 'logged in'">You are logged in</p>
    <p style="color: red;" v-if="loggedInState === 'login error'">Ошибка: неверны введены логин и пароль</p>
  </main>
</template>
