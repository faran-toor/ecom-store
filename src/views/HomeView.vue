<template>
  <div class="hero-section">
    <div class="upper">
      <div class="header-image">
        <div class="images">
          <div class="image1">
            <img src="/84770f_24595e0412cb42dfae6de1adbf5c73a1~mv2_d_1676_1980_s_2.png" alt="" />
            <div class="upper-content">
              <h1 class="title">New Outerwear Collection</h1>
              <button @click="addCart" class="shop-now">Show More</button>
            </div>
          </div>
          <div class="image2">
            <img src="/84770f_31b162dc5d2c487493fb435d6ddc9692~mv2.png" alt="" />
          </div>
        </div>
      </div>
    </div>
    <categories-home-page></categories-home-page>
    <filter-products></filter-products>
  </div>
  <!-- <div class="product" v-for="product in singleProduct" :key="product.id">
    <ProductsList :product="product" />
  </div> -->
</template>

<script>
import SideBarVue from '../components/sidebar/SideBar.vue'
import CategoriesHomePage from '../components/page/CategoriesHomePage.vue'
import FilterProducts from '../components/page/FilterProducts.vue'
export default {
  components: {
    SideBarVue,
    CategoriesHomePage,
    FilterProducts
  },
  data() {
    return {
      mobileApp: false
    }
  },
  computed: {
    singleProduct() {
      console.log(this.$store.getters.getCategories)
      return this.$store.getters.getSingleProduct
    }
  },
  created() {
    this.$store.dispatch('getCategories')
    window.scrollTo({
      top: 0
    })
  },
  mounted() {
    if (window.innerWidth < 450) {
      this.mobileApp = true
    } else if (window.innerWidth > 450) {
      this.mobileApp = false
    }
  },
  methods: {
    addCart() {
      this.$router.push({ path: '/all-products' })
    }
  }
}
</script>

<style scoped>
.header-image {
  position: relative;
  /* max-width: 820px; */
  /* margin: auto; */
  padding: 20px;
  overflow: hidden;
}
.images {
  display: flex;
  width: 100%;
}
.image1 {
  width: 55%;
  padding: 10px;
}
.image1 img {
  width: 100%;
  height: 900px;
}
.image2 {
  width: 45%;
}
.image2 img {
  position: relative;
  margin: 260px 0px 10px calc((100% - 490px) * 0.5);
  left: 74px;
}
.upper-content {
  position: absolute;
  left: 228px;
  bottom: 302px;
  width: 80%;
  z-index: 2;
}
.title {
  color: rgba(84, 84, 84, 0.65);
  text-align: center;
  font-size: 80px;
  font: normal normal normal 40px/1.4em futura-lt-w01-light, futura-lt-w05-light, sans-serif;
  text-transform: uppercase;
  position: absolute;
  bottom: 53px;
}
.shop-now {
  padding: 10px;
  text-align: center;
  font-size: 19px;
  width: 174px;
  background: #333333de;
  border: none;
  color: #fff;
  left: 194px;
  cursor: pointer;
}
.shop-now:hover {
  background: rgb(83 81 81 / 79%);
}
.mobile .header-image {
  position: relative;
  max-width: 820px;
  margin: auto;
  padding: 0px;
  overflow: hidden;
}
.mobile .images {
  display: block;
  width: 100%;
}
/* .mobile img[data-v-7d4f60e4] {
    width: 100%;
    height: 370px;
} */
.mobile .shop-now {
  padding: 10px;
  text-align: center;
  font-size: 19px;
  width: 174px;
  background: #333333de;
  border: none;
  color: #fff;
  left: 46px;
  bottom: 31px;
  cursor: pointer;
}
.mobile .title {
  color: rgba(84, 84, 84, 0.65);
  text-align: center;
  font: normal normal normal 35px/1.4em futura-lt-w01-light, futura-lt-w05-light, sans-serif;
  text-transform: uppercase;
  position: absolute;
  bottom: 84px;
  left: -85px;
}
.mobile .upper-content {
  position: absolute;
  left: 61px;
  bottom: 87px;
  width: 90%;
  /* z-index: 2; */
}
.mobile .image1 img {
  width: 100%;
  height: 100%;
}
.mobile .image1 {
  width: 100%;
  padding: 0px;
}
.mobile .image2 {
  width: 70%;
  margin: auto;
}

.mobile .image2 img {
  margin: 0;
  left: 0px;
  width: 100%;
}
</style>
