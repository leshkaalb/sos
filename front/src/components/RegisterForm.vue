<template>
  <div class="form">
    <h2>Регистрация</h2>
    <input v-model="username" placeholder="Имя пользователя" />
    <input v-model="password" type="password" placeholder="Пароль" />
    <button @click="register">Зарегистрироваться</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import axios from '../api/axios'
import { useRouter } from 'vue-router'

const username = ref('')
const password = ref('')
const router = useRouter()

const register = async () => {
  try {
    await axios.post('/registration', { username: username.value, password: password.value })
    alert('Регистрация успешна!')
    router.push('/login')
  } catch (err) {
    alert(err.response?.data?.message || 'Ошибка регистрации')
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
