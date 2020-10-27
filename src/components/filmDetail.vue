<template>
  <article>
    <div>
        <h1>{{film.title}}</h1>
            <dl>
                <dt>Director:</dt>
                <dd>{{film.director}}</dd>
                <dt>Synopsis:</dt>
                <dd>{{film.description}}</dd>
            </dl>
    </div>
    <div>
        <h3>List of characters</h3>
        <ul>
            <li v-for="(people, index) in people" :key=index :value="people">{{people.name}}</li>
        </ul>
    </div>
  </article>
</template>

<script>

export default {
    name: 'film-detail',
    props: ['film', 'people']

}
</script>

<style>

</style>