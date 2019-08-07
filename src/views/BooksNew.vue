<template>
  <div class="home">
    <p>Title: <input type="text" v-model="newTitle"></p>
    <p>Pages: <input type="text" v-model="newPages"></p>
    <button v-on:click="createBook()">Create</button>
  </div>
</template>

<style>
</style>

<script>
import axios from 'axios';
export default {
  data: function() {
    return {
      newTitle: '',
      newPages: ''
    };
  },
  created: function() {},
  methods: {
    createBook: function() {
      var newBook = {
        title: this.newTitle,
        pages: this.newPages
      };
      console.log(newBook);
      axios.post("api/books", newBook).then(response => {
        console.log(response.data);
        this.$router.push("/books");
      });
    }
  }
};
</script>