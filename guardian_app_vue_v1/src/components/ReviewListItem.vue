<template lang="html">
    <div class="reviewlistitem">
        <p>{{ review.webTitle }}</p>
    </div>
</template>

<script>
import { eventBus } from "@/main.js";

export default {
    name: "review-list-item",
    props: ['review'],
    // components: {
    //     ""
    methods: {
        displayInfo: function() {
            eventBus.$emit("review-selected", this.review);
        },
    }
    };

</script>

<style>

</style>