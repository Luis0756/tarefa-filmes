<template>
    <div>
      <h1>Cadastro de Filmes</h1>
      <form @submit.prevent="addMovie">
        <input type="text" v-model="newMovie.title" placeholder="Título" required />
        <input type="text" v-model="newMovie.genre" placeholder="Gênero" required />
        <input type="number" v-model="newMovie.year" placeholder="Ano" required />
        <button type="submit">Adicionar Filme</button>
      </form>
  
      <div v-if="movies.length === 0">
        <p>Nenhum filme cadastrado.</p>
      </div>
  
      <ul>
        <li v-for="(movie, index) in movies" :key="index">
          {{ movie.title }} ({{ movie.genre }}, {{ movie.year }})
          <button @click="removeMovie(index)">Deletar</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newMovie: {
          title: '',
          genre: '',
          year: null,
        },
        movies: [],
      };
    },
    methods: {
      addMovie() {
        this.movies.push({ ...this.newMovie });
        this.newMovie.title = '';
        this.newMovie.genre = '';
        this.newMovie.year = null;
      },
      removeMovie(index) {
        this.movies.splice(index, 1);
      },
    },
  };
  </script>
  
  <style scoped>

  input {
    margin: 5px;
  }
  button {
    margin-left: 10px;
  }
  </style>
  