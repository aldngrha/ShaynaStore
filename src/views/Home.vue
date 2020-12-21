<template>
  <div class="home">
    <HeaderShayna />
    <Hero />
    <WomenShayna />
    <Insta />
    <Partner />
    <Footer />
  </div>
</template>

<script>
// @ is an alias to /src
import HeaderShayna from "@/components/HeaderShayna.vue";
import Hero from "@/components/Hero.vue";
import WomenShayna from "@/components/WomenShayna.vue";
import Insta from "@/components/Insta.vue";
import Partner from "@/components/Partner.vue";
import Footer from "@/components/Footer.vue";
export default {
  name: "home",
  components: {
    HeaderShayna,
    Hero,
    WomenShayna,
    Insta,
    Partner,
    Footer,
  },
};
</script>
