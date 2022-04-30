<template>
  <div class="header">
    <nav class="header-navigation">
      <NuxtLink to="/login" class="nav-link">Login</NuxtLink>
      <NuxtLink to="/signup" class="nav-link">Signup</NuxtLink>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<style lang="scss" >
.header {
  width: 100%;
  height: 80px;
  color: white;
  align-items: center;
  display: flex;
  &-navigation {
    display: flex;
    height: 60px;
    justify-content: space-between;
    align-items: center;
    display: flex;
  }
}
.nav-link {
  color: white;
  text-decoration: none;
}

.logo {
  width: 200px;
  height: auto;
}
.logo-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>