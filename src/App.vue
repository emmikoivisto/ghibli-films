<template>
  <main>
    <film-list :films="films"></film-list>
    <!-- "films" comes from the data array -->
    <film-detail v-if="selectedFilm" :film="selectedFilm"></film-detail>
  </main>
</template>

<script>
import FilmList from '@/components/filmList';
import FilmDetail from '@/components/filmDetail';
import { eventBus } from '@/main.js'

export default {
  data() {
    return {
      films: [],
      characters: [],
      selectedFilm: null
    };
  },

  mounted() {
      this.fetchData();

      eventBus.$on('film-selected', (film) => {
        this.selectedFilm = film;
      });
  },
  methods: {
    fetchData: function() {
      fetch("https://ghibliapi.herokuapp.com/films")
      .then(res => res.json())
      .then(films => this.films = films);

      fetch("https://ghibliapi.herokuapp.com/people")
      .then(res => res.json())
      .then(characters => this.characters = characters);
    }
  },

  components: {
    FilmList,
    FilmDetail
  }
}
</script>

<style scoped>
main {
  
}
</style>