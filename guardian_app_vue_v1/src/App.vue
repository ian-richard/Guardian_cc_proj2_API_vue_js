<template>

  <div id="app">
      <!-- <p>{{this.seeData}}</p> -->
      <h1> Film reviews </h1>
      <div id="list" v-if="seeData.length">
        <review-list :seeData="seeData"></review-list>
        <h2>Film info</h2>
        <film-info
        v-if="selectedReview"
        :review="selectedReview">
        </film-info>

      </div>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
import ReviewList from "@/components/ReviewList";
import FilmInfo from "@/components/FilmInfo.vue";
import ReviewListItem from "@/components/ReviewListItem";

export default {
  name: 'app',
  components: {
    "review-list": ReviewList,
    "film-info": FilmInfo,
    "review-list-item": ReviewListItem
  },
  data() {
    return {
      seeData: [],
      selectedReview: null
    };
  },  
    methods: {
      fetchdata(){
        const promises = [1, 2].map(num => {
        return fetch("http://content.guardianapis.com/search?page=1&page-size=5&q=peter%20bradshaw&format=json&tag=film/film,tone/reviews&from-date=2010-01-01&order-by=newest&show-blocks=all&api-key=test"
        ).then(res => res.json());
        });
        
        Promise.all(promises)
          .then(data => {
            let reviewData = data.map (article => article.response.results);
            this.seeData = [...reviewData.flat(3)];
            console.log(this.seeData);
          })
    }
      },
      mounted(){
      this.fetchdata();

      eventBus.$on("review-selected", review => (this.selectedReview = review));
      
    }
  };


</script>

<style>
#list-info {
  display: flex;
}
</style>