<template>
  <div class="card-image">
    <img :src="src" :alt="alt" @load="onImageLoaded" />
  </div>
</template>

<script>
export default {
  props: ["src", "alt"],
  methods: {
    onImageLoaded() {
      this.$emit("imageLoaded");
    },
  },
};
</script>

<style scoped>
.card-image img {
  width: 300px;
  height: 200px;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
  object-fit: cover;
}
</style>
