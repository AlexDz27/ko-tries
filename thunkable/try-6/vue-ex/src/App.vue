<script setup>
import { ref, useTemplateRef } from 'vue'

const пользователи = [
  {
    логин: 'Оля',
    пароль: 'ol'
  },
  {
    логин: 'Вася',
    пароль: 'vas'
  },
]
let состояниеЛогина = ref('не залогинен')  // 'ошибка логина' | 'залогинен'
const логин = useTemplateRef('login')
const пароль = useTemplateRef('pwd')

function залогинить() {
  for (const пользователь of пользователи) {
    if (пользователь.логин === логин.value.value && пользователь.пароль === пароль.value.value) {
      состояниеЛогина.value = 'залогинен'
      return
    }
  }

  состояниеЛогина.value = 'ошибка логина'
}
</script>

<template>
  <main class="cont">
    <form @submit.prevent="залогинить">
      <p>Логин:</p>
      <input ref="login">
      <p>Пароль:</p>
      <input ref="pwd" type="password">
      <br>
      <br>
      <button type="submit">Войти ({{ состояниеЛогина }})</button>
    </form>

    <p style="color: green;" v-if="состояниеЛогина === 'залогинен'">Успех: Вы успешно вошли в систему</p>
    <p style="color: red;" v-if="состояниеЛогина === 'ошибка логина'">Ошибка: неверно введены логин и пароль</p>
  </main>
</template>
