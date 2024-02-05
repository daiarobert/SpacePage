<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">
        <img
          src="https://png.pngtree.com/png-vector/20190801/ourmid/pngtree-world-icon-png-image_1645053.jpg"
          alt="Logo"
          width="30"
          height="24"
          class="logo d-inline-block align-text-top"
        />
        Natural History Museum
      </a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNavAltMarkup"
        aria-controls="navbarNavAltMarkup"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
    </div>
  </nav>
</template>

<script>
export default {
  name: "NavbarComponent",
};
</script>

<style scoped lang="scss">
.navbar-brand {
  display: flex;
  align-items: center;

  .logo {
    height: 75px;
    width: 75px;
    margin-right: 15px;
  }
}
@media screen and (max-width: 405px) {
  .logo {
    height: 50px !important;
    width: 50px !important;
  }
}
</style>
