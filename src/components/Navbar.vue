<template>
  <nav class="main-navbar">
    <router-link :to="{ name: 'home' }">Home</router-link>
    <router-link :to="{ name: 'AddProject' }">Add Project</router-link>
  </nav>
</template>

<style>
.main-navbar {
  text-align: center;
  margin: 40px auto;
}
.main-navbar a {
  display: inline-block;
  text-decoration: none;
  color: #999;
  font-size: 18px;
  margin: 0 10px;
}
a.router-link-active {
  border-bottom: 2px solid teal;
  padding-bottom: 4px;
}
</style>
