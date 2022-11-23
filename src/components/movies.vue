<script setup>
import { ref } from "vue";
import axios from "axios";

const movies = ref("");
const response = ref(null);

const getMovie = async () => {
  const data = movie.value;
  response.value = (
    await axios.get("https://api.themoviedb.org/3/movie/${id}", {
      params: {
        api_key: "289d7511f89338dfaa9d5bc06621094c",
      },
    })
  ).data;
};
</script>

<template>
  <select v-model="movies">
    <option value="438148">Minions: The Rise of Gru</option>
    <option value="539681">DC League of Super-Pets</option>
    <option value="378236">The Emoji Movie</option>
    <option value="634649">Spider-Man: No Way Home</option>
    <option value="299536">Avengers: Infinity War</option>
    <option value="635302">Demon Slayer: Kimetsu no Yaiba – The Movie: Mugen Train</option>
    <option value="129">Spirited Away</option>
    <option value="8392">My Neighbor Totoro</option>
    <option value="135531">Fairy Tail the Movie: Phoenix Priestess</option>
    <option value="372058">Your Name.</option>
  </select>
  <button @click="getMovie">Get</button>
  <div v-if="response" class="movie-container">
    <p> {{ response.title }}</p>
    <p>Overview: {{ response.overview }}</p>
    <p>Original Language: {{ response.original_language }}</p>
    <p>Popularity: {{ response.popularity }}</p>
    <p>Vote Average: {{ response.vote_average }}</p>
  </div>
</template>