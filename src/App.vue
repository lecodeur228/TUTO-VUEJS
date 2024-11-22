
# la partie template est la partie html

<template>

  <p :style="{color: count >= 5 ? 'green' : 'red'}" :class="{active: count > 5}" > counteur : {{ count }}, <div v-html="firstName" ></div> </p>
  <!-- <div v-if="count >= 5" >Bravo vous avez cliqué plus de 5 fois</div>
  <div v-else>Bravo vous avez cliqué moins de 5 fois</div> -->
  <button @click="incr">increment</button>
  <button @click="decr">decrement</button>
  <hr>
  <button @click="sortMovies">Reorganiser</button>
  <form action="" @submit.prevent="addMovie">
    <input type="text" placeholder="Nom du film" v-model="movieName">
    <button>Ajouter</button>
  </form>
  <ul>
    <li v-for="movie in  movies" :key="movie" >
      {{ movie }} <button @click="deleteMovie(movie)"> supprimer</button>
    </li>
  </ul>

</template>

# la partie script est la partie js

<script setup>

import { ref } from 'vue'

const count = ref(0)

const movieName = ref("")

const firstName = "<span>John</span>"

const movies = ref( [
  "Titanic",
  "Avatar",
  "The Dark Knight",
  "The Godfather",
  "Pulp Fiction",
])

const deleteMovie = (movie) => {
  movies.value = movies.value.filter(m => m !== movie)
}

const sortMovies = () => {
  movies.value.sort((a,b) => a > b ? 1 : -1)
}

const incr = (event) => {
 
  count.value++
}
const decr = () => {
  count.value--
}

const addMovie = () => {

  movies.value.push(movieName.value)
  movieName.value = ""
}

</script>

# la partie style est la partie css
<style>

h1 {
  color: green;
}

.active {
  color: red;
}

</style>