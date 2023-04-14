<template>
  <div class="app">
    <the-header @add-cart="addCartShow" @show-menu-bar="showMenuBar"></the-header>
    <router-view v-slot="{ Component }">
      <transition name="route" made="out-in">
        <component :is="Component"></component>
      </transition>
    </router-view>
    <add-cart-page @close-cart="closeCart" v-if="showAddCartPage"></add-cart-page>
    <add-cart-mobile-icon v-if="iconMenu" @add-cart="addCartShow"></add-cart-mobile-icon>
    <scroll-up></scroll-up>
    <transition name="slide">
      <mobile-menu-bar
        v-if="showMenu"
        @close-menu-bar="closeMenuBar"
        @close-bar="closeMenuBar"
      ></mobile-menu-bar>
    </transition>
    <the-footer></the-footer>
  </div>
</template>

<script>
import TheHeader from './components/header/TheHeader.vue'
import AddCartPage from './components/page/AddCartSideBar.vue'
import ScrollUp from './components/icons/ScrollUp.vue'
import MobileMenuBar from './components/header/MobileMenuBar.vue'
import AddCartMobileIcon from './components/icons/AddCartMobileIcon.vue'
import TheFooter from './components/layout/TheFooter.vue'
export default {
  components: {
    TheHeader,
    AddCartPage,
    ScrollUp,
    TheFooter,
    MobileMenuBar,
    AddCartMobileIcon
  },
  data() {
    return {
      showSidebar: false,
      showAddCartPage: false,
      showMenu: false,
      iconMenu: false
    }
  },
  mounted() {
    if (window.innerWidth < 450) {
      this.iconMenu = true
    } else if (window.innerWidth > 450) {
      this.iconMenu = false
    }
  },
  methods: {
    showSideBar() {
      this.showSidebar = true
    },
    closeSideBar() {
      this.showSidebar = false
    },
    addCartShow() {
      this.showAddCartPage = true
      // document.querySelector('.add-cart').classList.toggle('active-icon')
    },
    closeCart() {
      document.querySelector('.add-cart').classList.toggle('close-cart')
      setTimeout(() => {
        // perform the task after the wait
        this.showAddCartPage = false
      }, 300)
      this.showAddCartPage = false
    },
    showMenuBar() {
      this.showMenu = true
    },
    closeMenuBar() {
      this.showMenu = false
    }
  }
}
</script>

<style>
.app {
  height: 100%;
  width: 100%;
}
.fixed-app {
  position: fixed;
}
.route-enter-from {
  opacity: 0;
  transform: translateX(100px);
}
.route-enter-to {
  opacity: 1;
  transform: translateX(0px);
}
.route-enter-active {
  transition: all 0.3s ease-in-out;
}
.route-leave-from {
  opacity: 1;
  transform: translateX(0px);
}
.route-leave-to {
  opacity: 0;
  transform: translateX(-100px);
}
.route-leave-active {
  transition: all 0.3s ease-in-out;
}
.slide-enter-active,
.slide-leave-active {
  transition: transform 0.5s;
}

.slide-enter,
.slide-leave-to {
  transform: translateX(100%);
}
</style>
