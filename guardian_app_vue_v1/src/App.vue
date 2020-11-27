<template>
  <h1>Test</h1>
</template>

<script>
export default {
  name: 'app',
  data(){
    return {
      stuff: [],

    }
  },  
    mounted(){
      this.fetchdata()
    },

  methods: {
    fetchdata(){
    fetch("http://content.guardianapis.com/search?page=1&page-size=150&q=peter%20bradshaw&format=json&tag=film/film,tone/reviews&from-date=2010-01-01&order-by=newest&show-blocks=all&api-key=test")
    .then(response => response.json())
    .then(data => this.stuff = data.response.results)
    },
  }
}
</script>

<style>

</style>