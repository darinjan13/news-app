<template>
  <v-app id="app">
      <Navbar />
    <v-app-bar app>
      <v-toolbar-title>News</v-toolbar-title>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-row no-gutters>
          <v-col>
            <Weather />
            <Home :articles="articles" />
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import axios from "axios";

import Home from "./components/Home";
import Weather from "./components/Weather";
import Navbar from "./components/Navbar";

export default {
  name: "App",

  components: {
    Navbar,
    Home,
    Weather,
  },

  data() {
    // var url = 'http://newsapi.org/v2/top-headlines?country=ph&';
    // var key = 'apiKey=b0008b5dd1614071a478c7756ee46fb4';

    return {
      userSearch: null,
      articles: [],
    };
  },
  mounted() {
    axios
      .get(
        "https://newsapi.org/v2/top-headlines?country=ph&apiKey=b0008b5dd1614071a478c7756ee46fb4"
      )
      .then((res) => {
        console.log(res.data.articles);
        this.articles = res.data.articles;
      });
  },
};
</script>
<style scoped>
#app {
  text-align: center;
}
</style>