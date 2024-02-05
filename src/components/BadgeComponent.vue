<template>
  <div class="badge">
    <img :src="imgSrc" alt="Partner Badge" />
  </div>
</template>

<script>
export default {
  props: {
    imgSrc: String,
  },
};
</script>

<style scoped lang="scss">
.badge {
  position: absolute;
  right: -35px;
  top: -25px;

  img {
    width: 50px;
  }
}
</style>
