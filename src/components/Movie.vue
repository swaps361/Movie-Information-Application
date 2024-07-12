<template>
  <div class="movie">
    <img :src="imageUrl" :alt="movie.Title">
    <div class="movie-info">
      <h2 class="movie-title">{{ movie.Title }}</h2>
      <p>Year: {{ movie.Year }}</p>
      <p>Type: {{ movie.Type }}</p>
      <button @click="showDetails">More Info</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    movie: Object
  },
  computed: {
    imageUrl() {
      return this.movie.Poster === 'N/A' ? '/assets/placeholder.jpg' : this.movie.Poster;
    }
  },
  methods: {
    showDetails() {
      this.$emit('more-info', this.movie.imdbID);
    }
  }
};
</script>

<style scoped>

.movie {
  border: 1px solid #ddd;
  border-radius: 5px;
  overflow: hidden;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
}

.movie img {
  width: 100%;
  height: auto;
}

.movie-title {
  padding: 10px;
  text-align: center;
}

.movie button {
  display: block;
  margin: 10px auto;
  padding: 10px 20px;
  background-color: #b82424;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.movie button:hover {
  background-color: #a04545;
}
</style>
