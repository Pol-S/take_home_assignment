

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h1>All quotes </h1>
    <div v-for="quote in quotes">
      <br>
      <h2>"{{ quote.quote }}"</h2>
      <p>Context: {{ quote.context }}
      Source: {{ quote.source }}
      Theme: {{ quote.theme }}</p>
    </div>
    {{quotes}}
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      quotes: [],
    };
  },
  created: function() {
    axios
      .get("https://gist.githubusercontent.com/benchprep/dffc3bffa9704626aa8832a3b4de5b27/raw/quotes.json")
      .then(response => {
        this.quotes = response.data;
      });
  },
  methods: {},
};
</script>
