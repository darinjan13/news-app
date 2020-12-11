<template>
  <div>
    <v-container>
      <v-row>
        <v-col>
          <v-card
            class="ma-sm-5 ma-lg-16"
            v-for="article in articles"
            :key="article.id"
          >
            <v-progress-linear height="30" color="white"></v-progress-linear>
            <v-img v-bind:src="article.urlToImage" class="mx-16" alt=""></v-img>
            <v-card-title class="ma-3">
              {{ article.title }}
            </v-card-title>
            <v-card-subtitle>{{ article.author }}</v-card-subtitle>
            <v-card-text>{{ article.description }}</v-card-text>
            <v-card-subtitle>
              <a :href="article.url" target="__blank">Click for more info...</a>
            </v-card-subtitle>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
    
  </div>
</template>

<script>
export default {
  props: {
    articles: Array,
  },
  methods: {},
};
</script>