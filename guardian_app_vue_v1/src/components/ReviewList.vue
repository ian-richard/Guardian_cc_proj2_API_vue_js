<template lang="html">
  <div class="review-list">
      <review-list-item
        v-for="(review, index) in seeData"
        :review="review"
        :key="index"
        >
        </review-list-item>
  </div>
</template>

<script>
import ReviewListItem from "@/components/ReviewListItem";

export default {
    name: "review-list",
    props: ["seeData"],
    components: {
        "review-list-item": ReviewListItem
    }
};
</script>

<style>
.review-list {
  width: 65%;
  height: 350px;
  overflow-y: scroll;
  display: flex;
  flex-wrap: wrap;
}
</style>