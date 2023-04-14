<template>
  <div class="mobile-bar" @click="$emit('close-menu-bar')">
    <router-link to="/">Home</router-link>
    <router-link :to="{ name: 'allProducts' }">Shop All</router-link>
    <router-link to="/about">About</router-link>
    <router-link to="/shipping-returns">Shipping Return's</router-link>
  </div>
</template>

<script>
export default {}
</script>

<style scoped>
.mobile-bar {
  position: absolute;
  top: 93px;
  left: 26px;
  display: flex;
  flex-direction: column;
}
.mobile-bar a {
  color: #fff;
  margin-left: 17px;
  text-decoration: none;
  font-size: 30px;
  font-weight: 400;
  margin-top: 22px;
}
</style>
