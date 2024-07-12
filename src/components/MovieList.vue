<template>
  <div class="movies-container">
    <Movie v-for="movie in movies" :key="movie.imdbID" :movie="movie" @more-info="showDetails" />
  </div>
</template>

<script>
import Movie from './Movie.vue';

export default {
  components: {
    Movie
  },
  props: {
    movies: Array
  },
  methods: {
    showDetails(imdbID) {
      this.$emit('more-info', imdbID);
    }
  }
};
</script>

<style scoped>
.movies-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 20px;
}
</style>
