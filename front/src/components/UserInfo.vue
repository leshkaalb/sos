<template>
  <div class="info" v-if="isAuth">
    <p>Вы вошли как <strong>{{ username }}</strong></p>
    <button @click="logout">Выйти</button>
  </div>
  <div v-else>
    <p>Вы не авторизованы</p>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const username = ref('')
const isAuth = ref(false)

onMounted(() => {
  const token = localStorage.getItem('token')
  const name = localStorage.getItem('username')
  if (token && name) {
    username.value = name
    isAuth.value = true
  }
})

const logout = () => {
  localStorage.removeItem('token')
  localStorage.removeItem('username')
  isAuth.value = false
  username.value = ''
}
</script>

<style scoped>
.info {
  text-align: center;
  margin-top: 20px;
}
</style>
