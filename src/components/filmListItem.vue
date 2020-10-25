<template>
  <li @click="handleClick">
      <p>{{film.title}}</p>
  </li>
</template>

<script>
import { eventBus } from '@/main.js';

export default {
    name: 'film-list-item',
    props: ['film'],
    
    methods: {
        handleClick: function(event) {
            eventBus.$emit('film-selected', this.film) //film comes from prop
        },
    },

}
</script>

<style scoped>
li {
    list-style: none;
    cursor: pointer;
}
</style>