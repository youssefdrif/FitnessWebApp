<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">
      <nav class="navbar">
        <div class="navbar-text">
          <RouterLink to="/">Home</RouterLink>
          <RouterLink to="/about">My stats</RouterLink>
          <RouterLink to="/about">Account</RouterLink>
        </div>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 16px;
  text-align: center;
  display: flex;
  align-items: center;
}

.navbar-text{
  font-size: 24px;
}

.navbar {
  background-color: #363636;
  height: 70px;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  margin-left: 32px;
}

nav a:first-of-type {
  border: 0;
}
</style>