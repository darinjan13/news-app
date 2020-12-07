<template>
    <div>
        <div v-for="article in articles" :key="article.id">
            <h1>{{ article.title }}</h1>
        </div>

    </div>
</template>

<script>
import axios from 'axios';
export default {
    data() {
        // var url = 'http://newsapi.org/v2/top-headlines?country=ph&';
        // var key = 'apiKey=b0008b5dd1614071a478c7756ee46fb4';

        return {
            articles: []
        }
    },
    methods: {
        
    },
    mounted() {
        axios.get('http://newsapi.org/v2/top-headlines?country=ph&apiKey=b0008b5dd1614071a478c7756ee46fb4')
        .then(res => {
            console.log(res.data.articles);
            this.articles = res.data.articles;
        })
    },
}
</script>