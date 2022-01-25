<template>
  <!-- Hero Section Begin -->
  <section class="hero-section">
    <carousel class="hero-items" :items="1" :nav="false" :autoplay="true">
      <div
        class="single-hero-items set-bg"
        style="background-image: url('/img/Header.png');"
      >
        <div class="container">
          <div class="row">
            <div class="col-lg-5">
              <span>Sunglasses</span>
              <h1>Calvin Klein</h1>
              <p>
                Started from Rp200.000,-
              </p>
              <a href="#" class="primary-btn">Shop Now</a>
            </div>
          </div>
        </div>
      </div>
      <div
        class="single-hero-items set-bg"
        style="background-image: url('/img/Header.png');"
      >
        <div class="container">
          <div class="row">
            <div class="col-lg-5">
              <span>Sunglasses</span>
              <h1>Calvin Klein</h1>
              <p>
                Started from Rp200.000,-
              </p>
              <a href="#" class="primary-btn">Shop Now</a>
            </div>
          </div>
        </div>
      </div>
      <div
        class="single-hero-items set-bg"
        style="background-image: url('/img/Header.png');"
      >
        <div class="container">
          <div class="row">
            <div class="col-lg-5">
              <span>Sunglasses</span>
              <h1>Calvin Klein</h1>
              <p>
                Started from Rp200.000,-
              </p>
              <a href="#" class="primary-btn">Shop Now</a>
            </div>
          </div>
        </div>
      </div>
    </carousel>
  </section>
  <!-- Hero Section End -->
</template>

<script>
import carousel from "vue-owl-carousel";

export default {
  name: "Hero",
  components: {
    carousel,
  },
};
</script>
