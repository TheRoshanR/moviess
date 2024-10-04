<template>
  <v-container>
    <template v-if="Object.keys(movieDetails).length">
      <v-row>
        <v-col>
          <v-img :src="movieDetails.Poster" height="600" contain />
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12">
          <div class="font-weight-bold">
            Title:
            <span class="font-weight-medium">{{ movieDetails.Title }}</span>
          </div>
        </v-col>
        <v-col cols="12">
          <div class="font-weight-bold">
            Genre:
            <span class="font-weight-medium">{{ movieDetails.Genre }}</span>
          </div>
        </v-col>
        <v-col cols="12">
          <div class="font-weight-bold">
            Director:
            <span class="font-weight-medium">{{ movieDetails.Director }}</span>
          </div>
        </v-col>
        <v-col cols="12">
          <div class="font-weight-bold">
            IMDB Rating:
            <span class="font-weight-medium">
              {{ movieDetails.imdbRating }}
            </span>
          </div>
        </v-col>
      </v-row>
    </template>

    <v-overlay :value="isLoading">
      <v-progress-circular indeterminate size="80" color="primary" />
    </v-overlay>
  </v-container>
</template>

<script>
import MovieService from '../services/MovieService.js'

export default {
  name: 'Movie',

  data() {
    return {
      movieDetails: {},
      isLoading: false,
    }
  },

  computed: {
    movieID() {
      return this.$route.params.id
    },
  },

  created() {
    this.getMovieDetails()
  },

  methods: {
    async getMovieDetails() {
      this.isLoading = true

      const response = await MovieService.getMovies(`i=${this.movieID}`)
      this.movieDetails = response.data

      this.isLoading = false
    },
  },
}
</script>
