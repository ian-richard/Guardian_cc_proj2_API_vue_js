<template>
  <p>{{this.seedata}}</p>
</template>

<script>
export default {
  name: 'app',
  data(){
    return {
      stuff: [],
      seedata: [],

    }
  },  
    mounted(){
      this.fetchdata();
    },

    // methods: {
    //   fetchdata(){
    //   fetch("http://content.guardianapis.com/search?page=1&page-size=150&q=peter%20bradshaw&format=json&tag=film/film,tone/reviews&from-date=2010-01-01&order-by=newest&show-blocks=all&api-key=test")
    //   .then(response => response.json())
    //   .then(data => this.stuff = data.response.results)
    //   },
    // }

    methods: {
      fetchdata(){
        const promises = [1].map(num => {
        return fetch("http://content.guardianapis.com/search?page=1&page-size=150&q=peter%20bradshaw&format=json&tag=film/film,tone/reviews&from-date=2010-01-01&order-by=newest&show-blocks=all&api-key=test"
        ).then(res => res.json());
        });
        
        Promise.all(promises)
          .then(data => {
            let reviewData = data.map (article => article.response.results);
            console.log(reviewData)
            // reviewData.flat(2);
            
            // reviewData.reduce(
            //   (flat, toFlatten) => flat.concat(toFlatten),
            //   []
            // );
            // console.log(data);
            console.log(reviewData.flat(3))
            this.seedata = [...reviewData.flat(3)];
          })
       
  
      }
    }


  }
    //   // get MVP working without promise, then come back to it later. 
     
        // }
        // .then(reviewData => this.stuff = data.response.results);

</script>

<style>

</style>