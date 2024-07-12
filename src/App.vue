<template>
  <div>
    <header>
      <h1>Movie Information Application</h1>
      <SearchBar @search="searchMovies" />
    </header>
    <main>
      <MovieList :movies="movies" @more-info="showMovieDetails" />
    </main>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
import MovieList from './components/MovieList.vue';

const API_KEY = 'a579d815';
const API_URL = 'https://www.omdbapi.com/';

export default {
  components: {
    SearchBar,
    MovieList
  },
  data() {
    return {
      movies: []
    };
  },
  methods: {
    async searchMovies(query) {
      try {
        const response = await axios.get(`${API_URL}?s=${query}&apikey=${API_KEY}`);
        this.movies = response.data.Search || [];
      } catch (error) {
        console.error('Error searching movies:', error);
      }
    },
    async showMovieDetails(imdbID) {
      try {
        const response = await axios.get(`${API_URL}?i=${imdbID}&apikey=${API_KEY}`);
        const movieDetails = response.data;
        alert(`Title: ${movieDetails.Title}\nYear: ${movieDetails.Year}\nType: ${movieDetails.Type}\nIMDb Rating: ${movieDetails.imdbRating}`);
      } catch (error) {
        console.error('Error fetching movie details:', error);
        alert('Failed to fetch movie details.');
      }
    }
  }
};
</script>

<style>
</style>
