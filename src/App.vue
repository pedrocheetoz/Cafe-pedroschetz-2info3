<template>
  <header class="header">
    <div class="container">
      <h2 class="logo">Coffee Ranking</h2>

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/avaliacao">Avaliações</RouterLink>
        <RouterLink to="/ranking">Ranking</RouterLink>
      </nav>
    </div>
  </header>

  <main class="content">
    <RouterView />
  </main>
</template>

<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #f4f6f9;
  font-family: Arial, Helvetica, sans-serif;
}


.header {
  position: fixed;
  top: 0;
  width: 100%;
  background: #FFFFE3;
  backdrop-filter: blur(8px);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
  z-index: 1000;
}

.container {
  max-width: 1200px;
  height: 70px;
  margin: auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 30px;
}

.logo {
  color: #6F4E37;
  font-size: 1.6rem;
}


nav {
  display: flex;
  gap: 25px;
}

nav a {
  color: #6F4E37;
  text-decoration: none;
  font-size: 1rem;
  font-weight: bold;
  padding: 8px 14px;
  border-radius: 8px;
  transition: 0.3s;
}

nav a:hover {
  background: #D1B399;
  transform: translateY(-2px);
}

nav a.router-link-active {
  background: #D1B399;
}


.content {
  margin-top: 90px;
  padding: 20px;
}
</style>
