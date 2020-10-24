<template>
  <article>
      <h1>{{film.title}}</h1>
      <dl>
          <dt>Director:</dt>
          <dd>{{film.director}}</dd>
          <dt>Synopsis:</dt>
          <dd>{{film.description}}</dd>
      </dl>
  </article>
</template>

<script>
export default {
    name: 'film-detail',
    props: ['film']
}
</script>

<style>

</style>