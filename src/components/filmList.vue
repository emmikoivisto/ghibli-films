<template>
  <div>
    <ul>
        <film-list-item 
        v-for="(film, index) in films" 
        :film='film' :key="index"></film-list-item>
<!-- first film="film" is naming the prop we'll use in list item, second one is pulling film from loop -->
    </ul>
  </div>
</template>

<script>
import FilmListItem from '@/components/filmListItem';

export default {
    name: 'film-list',
    components: {
        FilmListItem,
    },
    props: ['films'] //this is connected to app.vue :films="films"

}
</script>

<style>
ul {
    padding-left: 5px;
}
</style>