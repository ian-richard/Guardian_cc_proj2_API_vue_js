<template lang="html">
  <div class="review-list" v-if="seeData.length">
      <review-list-item
        v-for="(article, index) in seeData"
        :seeData="seeData"
        :key="index">
        </review-list-item>
  </div>
</template>

<script>
import ReviewListItem from "@/components/ReviewListItem";

export default {
    name: "review-list",
    props: ["seeData"],
    components: {
        "review-article-item": ReviewListItem
    }
};
</script>

<style>

</style>