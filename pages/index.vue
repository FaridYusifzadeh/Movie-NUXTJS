<template>
  <div class="home">
    <Hero />
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      movies: [],
    };
  },
  async fetch() {
    await this.getMovies();
  },
  methods: {
    async getMovies() {
      const data = axios.get(
        `https://api.themoviedb.org/3/movie/now_playing?api_key=37ed43a4f8eaa2abd75f9283692947bc&language=en-US&page=1`
      );
      const result = await data;
      result.data.results.forEach((item) => {
        this.movies.push(item);
      });
    },
  },
};
</script>
