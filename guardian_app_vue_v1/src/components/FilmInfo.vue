<template>
  <div id="film-info">
  <h4> {{review.webTitle}} </h4>
  <p>{{review.webPublicationDate}}</p>

  <p>{{review.blocks.body[0].bodyTextSummary}}</p>
  <img class="film-img" :src="review.blocks.main.elements[0].assets[3].file" />
  </div>
</template>

<script>
export default {
    props: ['review'],
    

}
</script>

<style>

</style>