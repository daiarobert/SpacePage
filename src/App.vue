<template>
  <div class="home-wrapper">
    <Navbar />
    <SpacePage />
  </div>
</template>

<script>
import Navbar from "./components/NavbarComponent.vue";
import SpacePage from "./pages/SpacePage.vue";

export default {
  name: "App",
  components: {
    SpacePage,
    Navbar,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.home-wrapper {
  max-width: 1300px;
  margin-left: auto;
  margin-right: auto;
}
</style>
