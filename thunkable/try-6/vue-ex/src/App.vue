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
let loggedInState = ref('не залогинен')  // 'ошибка логина' | 'залогинен'
const login = useTemplateRef('login')
const pwd = useTemplateRef('pwd')

function submit() {
  for (const user of users) {
    if (user.login === login.value.value && user.pwd === pwd.value.value) {
      loggedInState.value = 'залогинен'
      return
    }
  }

  loggedInState.value = 'ошибка логина'
}
</script>

<template>
  <main class="cont">
    <form @submit.prevent="submit">
      <p>Логин:</p>
      <input ref="login">
      <p>Пароль:</p>
      <input ref="pwd" type="password">
      <br>
      <br>
      <button type="submit">Войти ({{ loggedInState }})</button>
    </form>

    <p style="color: green;" v-if="loggedInState === 'залогинен'">Успех: Вы успешно вошли в систему</p>
    <p style="color: red;" v-if="loggedInState === 'ошибка логина'">Ошибка: неверны введены логин и пароль</p>
  </main>
</template>
