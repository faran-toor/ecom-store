<template>
  <div class="filter-section">
    <div class="header">
      <h1 class="title-header">New Arrivals</h1>
    </div>
    <div class="products-section">
      <div class="products-card" v-for="product in allProduct" :key="product.id">
        <div class="image" @click="addCart(product.id)">
          <img :src="product.thumbnail" alt="" />
          <button @click="addCart(product.id)" class="addcart-button">Add to cart</button>
        </div>
        <div class="title">
          <h3>{{ product.title }}</h3>
        </div>
      </div>
    </div>
    <div class="footer">
      <router-link to="/all-products"><button>Shop All</button></router-link>
    </div>
  </div>
</template>

<script>
export default {
  created() {
    this.$store.dispatch('filterProducts')
    // console.log(this.$store.getters.getFilterProducts)
  },
  computed: {
    allProduct() {
      return this.$store.getters.getFilterProducts
    }
  },
  methods: {
    addCart(id) {
      this.$router.push({ path: `/cart/${id}` })
    }
  }
}
</script>

<style scoped>
.filter-section {
  padding: 10px;
  margin-top: 2rem;
}
.products-section {
  display: flex;
  flex-wrap: wrap;
}
.products-card {
  width: 282px;
  height: 350px;
  padding: 5px;
  margin: 16px;
}
.products-card:hover {
  box-shadow: 0px 0px 20px 0px rgb(0 0 0 / 15%);
  border-radius: 10px;
}
.header {
  margin-bottom: 2rem;
  text-align: center;
  margin-left: 10px;
  margin-right: 10px;
}
.header::before {
  content: ' ';
  display: block;
  height: 1px;
  background-color: black;
  /* position: relative; */
  top: 22px;
  width: 37%;
}
.header::after {
  content: ' ';
  display: block;
  height: 1px;
  background-color: black;
  position: absolute;
  right: 0;
  top: 22px;
  width: 37%;
}
.mobile .header::before {
  /* no content */
  color: transparent;
  width: 0;
}
.mobile .header::after {
  /* no content */
  color: transparent;
  width: 0;
}
h1 {
  color: rgb(16 16 16);
}
.image {
  position: relative;
  transition: all 0.3s ease-in-out;
  overflow: hidden;
  height: 300px;
}
.mobile .image {
  cursor: pointer;
}
.addcart-button {
  position: absolute;
  bottom: 6px;
  right: 0;
  left: 0;
  width: 100%;
  padding: 5px;
  font-size: 30px;
  color: #ffffff;
  background: rgb(83 81 81 / 78%);
  border: 1px solid rgb(83 81 81);
  transition-duration: 399ms;
  transition-property: transform;
  transform: translateY(120%);
  cursor: pointer;
}
/* .addcart-button a{
  text-decoration: none;
  co
} */
.image:hover .addcart-button {
  transition-duration: 300ms;
  transform: translateY(20%);
}
img {
  width: 100%;
  height: 300px;
}
.title {
  color: #fff;
}
h3 {
  text-align: center;
  color: rgb(83 81 81 / 78%);
}
.footer {
  margin: 1rem;
}
.footer::before {
  content: ' ';
  display: block;
  height: 1px;
  background-color: black;
  /* position: relative; */
  top: 22px;
  width: 37%;
}
.footer::after {
  content: ' ';
  display: block;
  height: 1px;
  background-color: black;
  position: absolute;
  right: 0;
  top: 22px;
  width: 37%;
}
.mobile .footer::before {
  /* no content */
  color: transparent;
  width: 0;
}
.mobile .footer::after {
  /* no content */
  color: transparent;
  width: 0;
}
button {
  left: 42%;
  padding: 10px;
  width: 200px;
  font-size: 18px;
  border: 1px solid rgb(81, 81, 85);
  background: transparent;
  transition: all 0.3s ease-in-out;
  cursor: pointer;
}
.mobile button {
  left: 18%;
}
button:hover {
  background: rgb(81, 81, 85);
  color: #fff;
}
.mobile .products-section {
  display: block;
}
.mobile .products-card {
  height: 350px;
  margin: 1rem;
  width: 92%;
  padding: 0px;
}
</style>
