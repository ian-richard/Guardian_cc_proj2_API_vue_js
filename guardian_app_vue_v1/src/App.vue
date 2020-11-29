<template>

  <div id="app">
      <!-- <p>{{this.seeData}}</p> -->
      <h1> Film reviews </h1>
      <div id="list" v-if="seeData.length">
        <review-list :seeData="seeData"></review-list>
        <film-info
        :review="selectedReview">
        </film-info>

      </div>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
import ReviewList from "@/components/ReviewList";
import FilmInfo from './components/FilmInfo.vue';

export default {
  name: 'app',
  components: {
    "review-list": ReviewList,
  },
  data() {
    return {
      seeData: [],
      selectedReview: null
    };
  },  
    mounted(){
      this.fetchdata();

      eventBus.$on("review-selected", review => (this.selectedReview = review));
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
            // console.log(reviewData)
            // reviewData.flat(2);
            
            // reviewData.reduce(
            //   (flat, toFlatten) => flat.concat(toFlatten),
            //   []
            // );
            // console.log(data);
            // console.log(reviewData.flat(3))
            this.seeData = [...reviewData.flat(3)];
            console.log(this.seeData);
          })
      }
    }
  }


</script>

<style>
/* #list-info {
  display: flex;
} */
</style>