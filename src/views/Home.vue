<template>
  <div class="home">
    <Header />
    <Hero />
    <Post />
    <Insta />
    <Partner />
    <Footer />
  </div>
</template>

<script>
// @ is an alias to /src
import Header from "@/components/Header.vue";
import Hero from "@/components/Hero.vue";
import Post from "@/components/Post.vue";
import Insta from "@/components/Insta.vue";
import Partner from "@/components/Partner.vue";
import Footer from "@/components/Footer.vue";
export default {
  name: "home",
  components: {
    Header,
    Hero,
    Post,
    Insta,
    Partner,
    Footer,
  },
};
</script>
