<template>
  <header class="header">
    <Logo />
    <div class="nav-log">
      <NaveBar />
      <Login class="login" @add-cart="$emit('add-cart')" />
    </div>
    <div v-if="iconMenu" class="nav-mobile" @click="$emit('show-menu-bar')">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512">
        <!--! Font Awesome Pro 6.4.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2023 Fonticons, Inc. -->
        <path
          d="M32 288c-17.7 0-32 14.3-32 32s14.3 32 32 32l384 0c17.7 0 32-14.3 32-32s-14.3-32-32-32L32 288zm0-128c-17.7 0-32 14.3-32 32s14.3 32 32 32l384 0c17.7 0 32-14.3 32-32s-14.3-32-32-32L32 160z"
        />
      </svg>
    </div>
  </header>
</template>

<script>
import Logo from './Logo.vue'
import NaveBar from './NaveBar.vue'
import Login from './Login.vue'
export default {
  data() {
    return {
      iconMenu: false
    }
  },
  components: {
    Logo,
    NaveBar,
    Login
  },
  mounted() {
    if (window.innerWidth < 450) {
      this.iconMenu = true
      document.querySelector('.app').classList.add('mobile')
    } else if (window.innerWidth > 450) {
      this.iconMenu = false
      document.querySelector('.app').classList.remove('mobile')
    }
  },
  methods: {}
}
</script>

<style scoped>
.header {
  background-color: rgb(83, 81, 81);
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
  position: sticky;
  top: 0;
  z-index: 3;
}
.login {
  margin-left: 55px;
}
.nav-log {
  display: flex;
  margin-right: 20px;
}
@media (max-width: 450px) {
  .nav-log {
    display: none;
  }
}
.nav-mobile {
  width: 50px;
  height: 40px;
  background: white;
}
.nav-mobile svg {
  width: 40px;
  height: 40px;
  position: absolute;
  left: 4px;
}

/* .section-enter-from {
  top: 100vh;
}
.section-enter-to {
  top: 0;
}
.section-enter-active {
  transition: 0.5s;
}

.section-leave-from {
  top: 0;
}
.section-leave-to {
  top: -100vh;
}
.section-leave-active {
  transition: 0.5s;
} */
</style>
