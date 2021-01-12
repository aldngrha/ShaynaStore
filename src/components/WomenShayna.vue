<template>
  <!-- Women Banner Section Begin -->
  <section class="women-banner spad">
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-12 mt-5" v-if="products.length > 0">
          <carousel
            class="product-slider"
            :items="3"
            :dots="false"
            :nav="false"
            :autoplay="true"
          >
            <div
              class="product-item"
              v-for="itemProduct in products"
              :key="itemProduct.id"
            >
              <div class="pi-pic">
                <img :src="itemProduct.galleries[0].photo" alt="" />
                <ul>
                  <li
                    @click="
                      saveCart(
                        itemProduct.id,
                        itemProduct.name,
                        itemProduct.price,
                        itemProduct.galleries[0].photo
                      )
                    "
                    class="w-icon active"
                  >
                    <a href="#"><i class="icon_bag_alt"></i></a>
                  </li>
                  <li class="quick-view">
                    <router-link :to="'/product/' + itemProduct.id"
                      >+ Quick View</router-link
                    >
                  </li>
                </ul>
              </div>
              <div class="pi-text">
                <div class="catagory-name">{{ itemProduct.type }}</div>
                <a href="#">
                  <h5>{{ itemProduct.name }}</h5>
                </a>
                <div class="product-price">
                  ${{ itemProduct.price }}
                  <span>$35.00</span>
                </div>
              </div>
            </div>
          </carousel>
        </div>
        <div class="col-lg-12" v-else>
          <p>Maaf data baru belum tersedia</p>
        </div>
      </div>
    </div>
  </section>
  <!-- Women Banner Section End -->
</template>

<script>
import carousel from "vue-owl-carousel";
import axios from "axios";

export default {
  name: "WomenShayna",
  components: {
    carousel,
  },
  data() {
    return {
      products: [],
      cartUser: [],
    };
  },
  mounted() {
    axios
      .get("https://shayna.test/api/products")
      .then((res) => (this.products = res.data.data.data))
      .catch((err) => console.log(err));

    if (localStorage.getItem("cartUser")) {
      try {
        this.cartUser = JSON.parse(localStorage.getItem("cartUser"));
      } catch (e) {
        localStorage.removeItem("cartUser");
      }
    }
  },
  methods: {
    saveCart(idProduct, nameProduct, priceProduct, photoProduct) {
      let productStored = {
        id: idProduct,
        name: nameProduct,
        price: priceProduct,
        photo: photoProduct,
      };

      this.cartUser.push(productStored);
      const parsed = JSON.stringify(this.cartUser);
      localStorage.setItem("cartUser", parsed);

      window.location.reload();
    },
  },
};
</script>

<style scoped>
.product-item {
  margin-right: 25px;
}
</style>
