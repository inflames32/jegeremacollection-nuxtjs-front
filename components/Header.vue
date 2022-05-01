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
  data() {},
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
  margin-left: 32px;
  align-self: flex-start;
  margin-bottom: 32px;
  text-align: center;
  font-size: 16px;
  font-weight: bold;
  line-height: 30px;
  color: white;
  background-color: green;
  border: none;
  border-radius: 4px;
  text-decoration: none;
  padding: 6px 14px;
}
.nav-link:hover {
  background-color: rgb(16, 70, 16);
  transition: 0.3s;
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