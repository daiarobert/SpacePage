<template>
  <div class="space-page">
    <h1 class="space-page__title">Space</h1>
    <div class="row">
      <MuseumHighlight
        v-for="highlight in combinedHighlights"
        :key="highlight.id"
        :highlight="highlight"
        :badgeSrc="badgeSrc"
      />
    </div>
  </div>
</template>

<script>
import MuseumHighlight from "../components/MuseumHighlight.vue";
import _ from "lodash";

export default {
  components: {
    MuseumHighlight,
  },
  data() {
    return {
      loading: false,
      badgeSrc: "../assets/star.png",
      spaceHighlights: [
        {
          date: "2020-04-20 12:20:00",
          description:
            "Asteroids are minor planets, especially of the inner Solar System. Larger asteroids have also been called planetoids.",
          id: 1,
          image:
            "https://cdn.mos.cms.futurecdn.net/FiZPL85LFXAwM6StixFHUk-1200-80.jpg",
          name: "Asteroids",
        },
        {
          date: "2020-05-20 15:50:00",
          description:
            "A comet is an icy, small Solar System body that, when passing close to the Sun, warms and begins to release gases, a process called outgassing.",
          id: 9,
          image:
            "https://people.com/thmb/zq3mguZvu61vMGhYxzcxF3kz4Ig=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc():focal(668x353:670x355)/asteroid-near-earth-090623-tout-f03f82acbb4647a5a877c38567a065a7.jpg",
          name: "Comets",
        },
        {
          date: "2020-05-01 9:22:00",
          description:
            "The term planet is ancient, with ties to history, astrology, science, mythology, and religion.",
          id: 7,
          image:
            "https://astrobackyard.com/wp-content/uploads/2023/10/planets-in-order.jpg",
          name: "Planets",
          news: {
            date: "2020-08-18 18:00:00",
            title: "Attend our talk about Jupiter with Dr. Hogarth",
          },
          quiz: "https://planetquiz.space",
        },
        {
          date: "2020-07-05 4:10:00",
          description:
            "A meteor shower is a celestial event in which a number of meteors are observed to radiate, or originate, from one point in the night sky.",
          id: 12,
          image:
            "https://imageio.forbes.com/specials-images/imageserve/656bb721a5f8602a7b456f04/Star-shower/960x0.jpg?format=jpg&width=960",
          name: "Meteor showers",
          news: {
            title: "The Lyrids will peak at on April 21-22 2021, at night",
          },
        },
      ],
      spacePartners: {
        observatory: {
          createdAt: "2020-06-01 11:45:00",
          info: "The Mauna Kea Observatories (MKO) are a number of independent astronomical research facilities and large telescope observatories that are located at the summit of Mauna Kea on the Big Island of Hawaiʻi, United States.  ",
          image:
            "https://bigislandguide.com/wp-content/uploads/2017/11/home-mauna-kea@1x-1500x751.jpg",
          name: "Mauna Kea Observatories",
        },
      },
    };
  },
  computed: {
    combinedHighlights() {
      // Convert spacePartners object into an array of its values
      const partnersArray = Object.values(this.spacePartners).map(
        (partner) => ({
          ...partner,
          date: partner.createdAt, // Map createdAt to date
          description: partner.info, // Map info to description
          id: `partner-${partner.name}`, // Create a unique ID
          isPartner: true,
        })
      );

      // Merge the transformed partnersArray with spaceHighlights
      const allHighlights = [...this.spaceHighlights, ...partnersArray];

      // Sort all highlights by date
      return _.orderBy(
        allHighlights,
        (highlight) => new Date(highlight.date),
        "desc"
      );
    },
  },
};
</script>

<style lang="scss" scoped>
.space-page {
  .wrapper {
    display: flex;
  }
  &__title {
    color: #2c3791;
    font-size: 24px;
    font-weight: 600;
    margin-top: 20px;
  }
}
</style>
