<template>
  <main>
    <film-list :films="films"></film-list>
    <!-- "films" comes from the data array -->
    <film-detail v-if="selectedFilm" :film="selectedFilm"  :people="people"></film-detail>
  </main>
</template>

<script>
import FilmList from '@/components/filmList';
import FilmDetail from '@/components/filmDetail';
import favouriteFilms from '@/components/favouriteFilms';
import { eventBus } from '@/main.js';


export default {
  data() {
    return {
      films: [],
      people: [],
      selectedFilm: null,
      favouriteFilms: []
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
      .then(people => this.people = people);
    },

    addToFavourites: function() {
      this.favouriteFilms.push(this.selectedFilm)
    }
  },

  components: {
    FilmList,
    FilmDetail,
    favouriteFilms
  }
}
</script>

<style scoped>
main {
  display: grid;
  height: 100vh;
  grid-template-columns: 7fr 13fr;

}
</style>