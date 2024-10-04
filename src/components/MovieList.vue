<template>
  <v-layout row wrap>
    <template v-if="movies.length">
      <v-flex xs12 sm6 md4 lg3 v-for="movie in movies" :key="movie.id">
        <movie-card :movie="movie" />
      </v-flex>
    </template>

    <v-layout v-else align-center justify-center row wrap>
      No movie to show.
    </v-layout>
  </v-layout>
</template>

<script>
import MovieCard from './MovieCard.vue'

export default {
  name: 'MovieList',

  components: {
    MovieCard,
  },

  props: {
    movies: {
      type: Array,
      required: true,
    },
  },
}
</script>
