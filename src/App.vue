<template>
  <nav class="navbar">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav>
  <router-view/>
</template>

<style>
#app {
  margin: 0;
  padding: 0;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body{
  background: linear-gradient(to right, #1e0303, #061033);
  top: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  height: 100vh;
}


nav {
  font-size: 20px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;

}

nav a.router-link-exact-active {
  color: turquoise;
}
.navbar {
  position: absolute;
  display: flex;
  top: 30px;
  right: 30px;
  padding: 10px;
}
</style>
