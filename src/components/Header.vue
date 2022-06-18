<template>
  <div id="map">
    <div class="wrapper">
      <h1>ATLAS</h1>
      <b-button
        class="home-button"
        variant="outline-warning"
        href="https://zqlimy.com"
        >Home</b-button
      >
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style lang="sass" scoped>
#map
  position: absolute
  top: 0
  z-index: 2
  width: 100%
  text-align: center
  .wrapper
    position: relative
    h1
      margin: 0
      color: azure
    .home-button
      position: absolute
      right: 10px
      top: 10px
</style>
