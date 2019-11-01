<template>
  <div id="app">
    <Home msg="JAGGY JAH"/>
  </div>
</template>

<style lang="css">
@import "./assets/css/animate.min.css";
@import "./assets/css/style.css";
</style>

<script>
import Home from "./components/Home.vue"

export default {
  name: 'app',
  components: {
    Home
  }
}
</script>
