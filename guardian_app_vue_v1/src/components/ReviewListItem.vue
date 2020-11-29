<template lang="html">
    <div class="reviewlistitem">
        <p>{{ review.webTitle }}</p>
        <button v-on:click="displayInfo">More info</button>
    </div>
</template>

<script>
import { eventBus } from "@/main.js";

export default {
    name: "review-list-item",
    props: ['review'],
    methods: {
        displayInfo: function() {
            eventBus.$emit("review-selected", this.review);
        }
    }
    };

</script>

<style>

</style>