<template>
  <div id="body">
    <Carousel
      class="d-flex justify-content-center"
      :per-page="6"
      :paginationEnabled="false"
      :navigationEnabled="true"
      loop
    >
      <Slide class="slide" v-for="(value, k) in responseData" :key="k">
        <b-card
          :img-src="value.trailer"
          img-height="320"
          style="max-width: 20rem"
          img-top
          class="mb-2 center"
          no-body
          v-b-modal.my-modal
        >
        </b-card>
        <p>
          {{ value.language }}
        </p>
        <b-modal id="my-modal"
          ><iframe
            width="420"
            height="280"
            src="https://www.youtube.com/embed/Kbm9HsF_7-4?autoplay=true"
            title="Vue js tutorial for beginners  #22 fetch data from API | axios"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
            allowfullscreen
          ></iframe>
        </b-modal>
      </Slide>
    </Carousel>
  </div>
</template>

<script>
import axios from "axios"
import { Carousel, Slide } from "vue-carousel"

export default {
  data() {
    return {
      responseData: null,
    }
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

<style>
.VueCarousel-navigation-button {
  color: inherit !important;
}
.Vuecarousel-navigation-button {
  color: #ffffff !important;
}
#body {
  width: 98%;
  height: 100%;
  margin: 0.5%;
  padding: 1%;
}
</style>
