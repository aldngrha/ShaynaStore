<template>
  <header class="header-section">
    <div class="container">
      <div class="inner-header">
        <div class="row">
          <div class="col-lg-2 col-md-2">
            <div class="logo">
              <router-link to="/">
                <img src="img/logo_bening.png" alt="" />
              </router-link>
            </div>
          </div>
          <div class="col-lg-7 col-md-7">
            <nav class="navbar navbar-expand-lg navbar-light">
              <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
                <div class="navbar-nav mx-auto">
                  <a class="nav-link active" href="#"
                    >Home <span class="sr-only">(current)</span></a
                  >
                  <a class="nav-link" href="#">Sunglasses</a>
                  <a class="nav-link" href="#">Eyeglasses</a>
                  <a class="nav-link" href="#">Contacts</a>
                </div>
              </div>
            </nav>
          </div>
          <div class="col-lg-3 text-right col-md-3">
            <ul class="nav-right">
              <li class="cart-icon">
                Keranjang Belanja &nbsp;
                <a href="#">
                  <i class="icon_bag_alt"></i>
                  <span>{{ cartUser.length }}</span>
                </a>
                <div class="cart-hover">
                  <div class="select-items">
                    <table>
                      <tbody v-if="cartUser.length > 0">
                        <tr v-for="cart in cartUser" :key="cart.id">
                          <img class="photo-item" :src="cart.photo" alt="" />
                          <td class="si-pic"></td>
                          <td class="si-text">
                            <div class="product-selected">
                              <p>${{ cart.price }} x 1</p>
                              <h6>{{ cart.name }}</h6>
                            </div>
                          </td>
                          <td @click="removeItem(cart.id)" class="si-close">
                            <i class="ti-close"></i>
                          </td>
                        </tr>
                      </tbody>
                      <tbody v-else>
                        <tr>
                          <td>Keranjang kosong</td>
                        </tr>
                      </tbody>
                    </table>
                  </div>
                  <div class="select-total">
                    <span>total:</span>
                    <h5>${{ priceTotal }}.00</h5>
                  </div>
                  <div class="select-button">
                    <a href="#" class="primary-btn view-card"
                      ><router-link to="/cart" style="color: #fff;"
                        >VIEW CARD</router-link
                      ></a
                    >
                    <a href="#" class="primary-btn checkout-btn">CHECK OUT</a>
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      cartUser: [],
    };
  },
  methods: {
    removeItem(idx) {
      // cari tahu id dari item yang akan dihapus
      let cartUserStorage = JSON.parse(localStorage.getItem("cartUser"));
      let itemCartUserStorage = cartUserStorage.map(
        (itemCartUserStorage) => itemCartUserStorage.id
      );

      // cocokkan idx item dengan id yang ada di storage
      let index = itemCartUserStorage.findIndex((id) => id == idx);
      this.cartUser.splice(index, 1);

      const parsed = JSON.stringify(this.cartUser);
      localStorage.setItem("cartUser", parsed);
      window.location.reload();
    },
  },
  mounted() {
    if (localStorage.getItem("cartUser")) {
      try {
        this.cartUser = JSON.parse(localStorage.getItem("cartUser"));
      } catch (e) {
        localStorage.removeItem("cartUser");
      }
    }
  },
  computed: {
    priceTotal() {
      return this.cartUser.reduce(function(items, data) {
        return items + data.price;
      }, 0);
    },
  },
};
</script>

<style scoped>
.photo-item {
  width: 70px;
}
</style>
