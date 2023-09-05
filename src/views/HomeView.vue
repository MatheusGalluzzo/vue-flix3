<template>
  <div class="home">
    <h1 style="font-size: 35px"></h1>
    <movies-section :movies="movies" />
    <!-- <div v-for="(value, k) in responseData" :key="k"> -->
    <!-- </div> -->
  </div>
</template>

<style scoped>
p {
  font-size: 12.5pt;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  text-align: center;
}

.carousel {
  margin-top: 100px;
  display: flex;
  justify-content: center !important;
}
.slide {
  border: 1px solid white;
  border-radius: 8px;
  transition: transform 500ms;
}
.slide:hover {
  transform: scale(1.05);
}
</style>
<script>
import axios from "axios";
import { Carousel, Slide } from "vue-carousel";

export default {
  data() {
    return {
      responseData: null,
    };
  },
  components: {
    Carousel,
    Slide,
  },
  mounted() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      axios
        .get("http://localhost:51828/api/v1/movies") // Note the lowercase 'localhost'
        .then((response) => {
          this.responseData = response.data;
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
};
</script>
