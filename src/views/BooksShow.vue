<template>
  <div class="home">
    <p> Title: {{ book.title }} </p>
    <p> Pages: {{ book.pages }} </p>
    <router-link v-bind:to="`/books/${book.id}/edit`">Edit</router-link>
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
      book: []
    };
  },
  created: function() {
    axios.get(`api/books/${this.$route.params.id}`).then(response => {
      this.book = response.data;
    });
  },
  methods: {}
};
</script>