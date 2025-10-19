<template>
  <div>
    <nav>
      <router-link to="/register">Регистрация</router-link> |
      <router-link to="/login">Авторизация</router-link>
    </nav>
    <router-view />
  </div>
</template>

<style>
body {
  font-family: sans-serif;
  background: #fafafa;
}
nav {
  margin: 20px;
  text-align: center;
}
a {
  text-decoration: none;
  margin: 0 10px;
  color: #42b983;
}
a.router-link-exact-active {
  font-weight: bold;
}
</style>
