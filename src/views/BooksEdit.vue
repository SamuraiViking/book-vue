<template>
  <div class="home">
    <p>{{ book.title }}</p>
    <p>{{ book.pages }}</p>
    <p>Title: <input type="text" v-model="newTitle"></p>
    <p>Pages: <input type="text" v-model="newPages"></p>
    <button v-on:click="editBook">update</button>
  </div>
</template>

<style>
</style>

<script>
import axios from 'axios';
export default {
  data: function() {
    return {
      book: '',
      newTitle: '',
      newPages: ''
    };
  },
  created: function() {
    axios.get(`api/books/${this.$route.params.id}`).then( response => {
      this.book = response.data;
    });
  },
  methods: {
    editBook: function() {
      var newBook = {
        title: this.newTitle,
        pages: this.newPages
      };
      axios.patch(`api/books/${this.$route.params.id}`, newBook).then(response => {
        this.$router.push('/books');
      });
    }
  }
};
</script>