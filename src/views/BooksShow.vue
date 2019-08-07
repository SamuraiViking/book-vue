<template>
  <div class="home">
    <p> Title: {{ book.title }} </p>
    <p> Pages: {{ book.pages }} </p>
    <router-link v-bind:to="`/books/${book.id}/edit`">Edit</router-link>
    <div>
      <button v-on:click="destroyBook(book)">Destroy</button>
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
      book: []
    };
  },
  created: function() {
    axios.get(`api/books/${this.$route.params.id}`).then(response => {
      this.book = response.data;
    });
  },
  methods: {
    destroyBook: function(theBook) {
      axios.delete(`api/books/${theBook.id}`).then(response => {
        this.$router.push("/books");
      });
    }
  }
};
</script>