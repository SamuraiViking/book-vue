<template>
  <div class="home">
    <div v-for="book in books">
      <p> Title: {{ book.title }} </p>
      <p> Pages: {{ book.pages }} </p>
      <router-link v-bind:to="`/books/${book.id}`">more info</router-link>
      <hr>
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from 'axios';
export default {
  data: function() {
    return {
      message: "welcome to books!",
      books: []
    };
  },
  created: function() {
    axios.get('api/books').then(response => {
      this.books = response.data;
    });
  },
  methods: {}
};
</script>