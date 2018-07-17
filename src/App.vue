<template>
  <div class="container">
    <!-- <div id="app"> -->

			<div v-for="article in news">
        <img :src="article.urlToImage" alt="">
        <h3>{{article.title}}</h3>
        <h4>{{article.author}}</h4>
        <p>{{article.description}}</p>
        <a class="button" :href="article.url" target="_blank">read more</a>

    
 
  </div>
<!-- </div> -->
  </div>
</template>

<script>

import axios from 'axios'

const url = "https://newsapi.org/v2/top-headlines?country=us&category=business&apiKey=b76c09e8991f4c5b98b3951352db03c7";

const data = {
  news:[]
}

export default {
  data: function() {
    return data
    
    },
    created(){
    	this.loadNews();
    },

    methods:{
    	 loadNews(){
    axios.get(url).then(function(response) {
      console.log(response.data.articles)
     data.news = response.data.articles
     
    }).catch(function(error){
      console.log(error.message)
    })
  }
  }
    
  }

</script>
