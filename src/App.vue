<template>
  <b-container id="app">
    <Header />
    <Map />
    <Footer />
  </b-container>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import Map from "./components/Map.vue";
export default {
  name: "App",
  components: { Header, Footer, Map },
};
</script>

<style lang="sass" scoped>
*
  outline: 1px solid gold
  outline-offset: -1px
#app
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  color: #2c3e50
</style>
