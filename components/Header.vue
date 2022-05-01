<template>
  <div class="header">
    <nav class="header-navigation">
      <NuxtLink to="/" class="nav-link">Home</NuxtLink>
      <NuxtLink to="/login" class="nav-link">Login</NuxtLink>
      <NuxtLink to="/signup" class="nav-link">Signup</NuxtLink>
      <NuxtLink to="/user/:userid" class="nav-link">{{ email }}</NuxtLink>

      <div class="burger-icon-close" @click="openMenu">
        <span v-if="!menuIsOpen" class="icon-close">|||</span>
        <span v-else class="icon-open">X</span>
      </div>
    </nav>
    <nav class="mobile-navigation" v-if="menuIsOpen">
      <NuxtLink to="/" class="nav-link">Home</NuxtLink>
      <NuxtLink to="/login" class="nav-link">Login</NuxtLink>
      <NuxtLink to="/signup" class="nav-link">Signup</NuxtLink>
      <NuxtLink to="/user/:userid" class="nav-link">{{ email }}}}</NuxtLink>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      menuIsOpen: false,
      test: {},
      email: '',
    }
  },
  methods: {
    openMenu() {
      this.menuIsOpen = !this.menuIsOpen
      console.log(this.menuIsOpen)
    },
  },
}
</script>

<style lang="scss" >
@media (min-width: 750px) {
  .mobile-menu {
    display: none;
  }
}
.mobile-menu {
  display: flex;
}

.icon-close,
.icon-open {
  @media (max-width: 750px) {
    display: flex;
    justify-content: center;
    align-content: center;
    color: black;
    font-size: 32px;
    height: 80px;
    width: 80px;
    position: absolute;
    right: 20px;
    top: 20px;
    color: white;
    transform: rotate(90deg);
  }
  @media (min-width: 751px) {
    display: none;
  }
}

.header {
  background-color: grey;
  @media (max-width: 750px) {
    width: 100%;
    height: 80px;
  }
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
    @media (max-width: 750px) {
      display: none;
    }
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

.burger-icon-close {
  display: flex;
  justify-content: center;
  align-content: center;
  color: black;
  font-size: 32px;
  height: 80px;
  width: 80px;
}
</style>