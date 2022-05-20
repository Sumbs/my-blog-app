<template>
  <div class="q-pa-md">
    <h4>haha</h4>
    
  </div>
</template>

<script>
import { defineComponent } from "vue";
import BlogEntry from "components/BlogEntry.vue";

const blogsList = [
  {
    title: "Why do Squirrels Love Nuts so Much? A Deep Dive",
    year: 2000,
    month: 1,
    day: 16,
    content: "Squirrels really love nuts. But why? WHY?!?!?!? ......",
    author: "John Doe",
    id: 1,
  },
  {
    title: "Why Not Everybody Deserves Rights",
    year: 2022,
    month: 11,
    day: 31,
    content:
      "Humans have had it too easy in the last century. They need to stop.",
    author: "Justin Time",
    id: 2,
  },
];

export default defineComponent({
  name: "BlogEntryPage",

  data() {
    return {
        blogEntry: blogsList.find((entry) => {
            return entry === this.$route.params.id
        })
    };
  },
});
</script>
