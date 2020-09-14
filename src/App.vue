<template>
  <div id="app">
    <Header />
    <Map />
    <Footer />
  </div>
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

#app
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  color: #2c3e50
  background-color: slategrey
  height: 100vh
</style>
