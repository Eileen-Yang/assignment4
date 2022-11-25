<script setup>
import { ref } from "vue";
import axios from "axios";

const movies = ref("");
const response = ref(null);

const getData = async (url, params) => {
  try {
    return await axios.get(url, params);
  } catch (error) {
    console.log(error);
  }
};

const getMovies = async () => {
  response.value = (await axios.get(`https://api.themoviedb.org/3/movie/${movies.value}`, {
    params: {
      api_key: "289d7511f89338dfaa9d5bc06621094c",
    },
  })).data;
};
</script>

<template>
  <header>Movies</header>
  <label>Choose a Movie:</label>
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
  <button @click="getMovies">Get</button>
  <div v-if="response" class="movies-container">
    <p> {{ response.title }}</p>
    <p>Overview: {{ response.overview }}</p>
    <p>Release Date: {{ response.release_date }}</p>
    <p>Original Language: {{ response.original_language }}</p>
    <p>Popularity: {{ response.popularity }}</p>
    <p>Vote Average: {{ response.vote_average }}/10.0</p>
    <p>Vote Count: {{ response.vote_count }}</p>
    <p>Revenue: ${{ response.revenue }}</p>
    <img :src="`https://image.tmdb.org/t/p/w500/${response.poster_path}`" />
    <img :src="`https://image.tmdb.org/t/p/w500/${response.backdrop_path}`" />
  </div>
</template>

<style scoped>
* {
  font-size: 100%;
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
  margin-top: 0px;
  margin-bottom: 25px;
  margin-left: 0px;
  margin-right: 0px;
}

header {
  margin: 0px;
  font-family: 'Anton', sans-serif;
  font-size: 350%;
  text-align: center;
}

label {
  font-weight: bold;
  font-family: 'Times New Roman', Times, serif;
  font-size: 150%;
  margin-top: 5px;
  margin-left: 10px;
}

/*select#Movies {
  margin-top: 5px;
  font-size: 130%;
}*/

select {
  width: 100%;
}

option {
  font-family: Georgia, 'Times New Roman', Times, serif;
}

div {
  width: 100%;
  margin-left: 10px;
  font-size: 135%;
}

img {
    position: relative;
    width: 45%;
    margin-right: 25px;
    margin-left: 25px;
  }
  
</style>