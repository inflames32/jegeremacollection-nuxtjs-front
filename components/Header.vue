<template>
  <div class="header">
    <nav class="header-navigation">
      <div class="logo">
        <img src="@/assets/images/logo.jpg" alt="" class="logo-img" />
      </div>
      <NuxtLink to="/" class="nav-link">Accueil</NuxtLink>
      <NuxtLink to="/login" class="nav-link">Login</NuxtLink>
      <NuxtLink to="/signup" class="nav-link">Créer mon compte</NuxtLink>
      <NuxtLink to="/albumspublics" class="nav-link">Albums Publics</NuxtLink>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<style >
.header {
  width: 100%;
  height: 80px;
  color: white;
}
.header-navigation {
  display: flex;
  height: 60px;
  justify-content: space-between;
}
a {
  color: white;
  text-decoration: none;
}
a:hover {
  background-color: rgb(43, 177, 43);
}

.nuxt-link-exact-active,
.nuxt-link-active {
  background-color: #f0f;
  color: white;
  text-decoration: none;
}
img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>