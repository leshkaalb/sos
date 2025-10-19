<template>
  <div class="form">
    <h2>Авторизация</h2>
    <input v-model="username" placeholder="Имя пользователя" />
    <input v-model="password" type="password" placeholder="Пароль" />
    <button @click="login">Войти</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import axios from '../api/axios'
import { useRouter } from 'vue-router'

const username = ref('')
const password = ref('')
const router = useRouter()

const login = async () => {
  try {
    const res = await axios.post('/login', { username: username.value, password: password.value })
    localStorage.setItem('token', res.data.token)
    localStorage.setItem('username', username.value)
    router.push('/login')
  } catch (err) {
    alert(err.response?.data?.message || 'Ошибка входа')
  }
}
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  width: 250px;
  margin: 50px auto;
}
input, button {
  margin: 5px 0;
  padding: 5px;
}
</style>
