<template>
  <div class="highlight-card col-xl-3 col-lg-4 col-md-6 col-12">
    <div
      class="card-inner"
      :class="{ 'card-inner--partner': highlight.isPartner }"
    >
      <Badge :imgSrc="badgeSrc" />
      <CardImage
        :src="imageSrc"
        :alt="highlight.name"
        @imageLoaded="handleImageLoaded"
      />
      <h3 class="highlight-card__title">{{ highlight.name }}</h3>
      <p class="highlight-card__description">{{ highlight.description }}</p>

      <div v-if="highlight.news">
        <h5>News:</h5>
        <p>{{ highlight.news.title }}</p>
      </div>
      <div class="badge">
        <img src="../assets/star.png" />
      </div>
      <a
        v-if="highlight.quiz"
        :href="highlight.quiz"
        class="btn btn-success mb-3"
        target="_blank"
      >
        Take Quiz
      </a>
      <button
        class="refresh-button btn btn-primary"
        @click="refreshImage"
        :disabled="loading"
      >
        {{ loading ? "Loading..." : "Refresh Image" }}
      </button>
    </div>
  </div>
</template>

<script>
import CardImage from "./CardImage.vue";

export default {
  components: { CardImage },
  props: {
    highlight: Object,
    badgeSrc: String,
  },
  data() {
    return {
      imageSrc: this.highlight.image,
      loading: false,
    };
  },
  methods: {
    async refreshImage() {
      this.loading = true;
      this.imageSrc = await this.fetchNewImageUrl(this.highlight.name);
      // Do not set loading = false here. It will be set in handleImageLoaded
    },
    handleImageLoaded() {
      this.loading = false; // Set loading false only after the image has loaded
    },
    fetchNewImageUrl(name) {
      const processedName = name.toLowerCase().replace(/\s+/g, "-");
      return new Promise((resolve) => {
        setTimeout(() => {
          const timestamp = new Date().getTime();
          resolve(
            `https://source.unsplash.com/random/800x600?${processedName}&sig=${timestamp}`
          );
        }, 1500); // Simulated delay
      });
    },
  },
};
</script>

<style scoped lang="scss">
.highlight-card {
  padding: 0;
  display: flex;
  justify-content: center;
  min-height: 550px;

  &__description {
    padding: 0 15px;
  }
}

.card-inner {
  border: 1px solid #ccc;
  border-radius: 8px;
  position: relative;
  margin: 10px;
  max-width: 300px;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  background-color: #ffffff;

  box-shadow: 0 19px 38px rgba(0, 0, 0, 0.3), 0 15px 12px rgba(0, 0, 0, 0.22);

  &--partner {
    box-shadow: 0px 19px 27px 32px rgba(3, 239, 255, 0.3);
  }
}

.refresh-button {
  margin-top: auto;
  padding: 5px 20px;
  border-radius: 5px;
  color: white;
  cursor: pointer;
  margin-bottom: 20px;
}

h3 {
  margin-top: 25px;
}

.badge img {
  width: 50px;
}
.badge {
  position: absolute;
  right: -35px;
  top: -25px;
}
</style>
