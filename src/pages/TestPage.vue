<template>
  <div class="q-pa-md">
    <q-input outlined v-model="search" label="Search Blogs" class="q-pa-md"/>
    <q-list bordered separator>
      <q-item-label header> Blogs </q-item-label>
      <BlogEntry
        v-for="entry in filteredBlogs"
        :key="entry.title"
        v-bind="entry"
      />
    </q-list>
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
    content: "Humans have had it too easy in the last century. They need to stop.",
    author: "Justin Time",
    id: 2,
  },
];

export default defineComponent({
  name: "TestPage",

  components: {
    BlogEntry,
  },

  data() {
    return {
      blogEntries: blogsList,
      search: "",
    };
  },

  computed: {
    filteredBlogs: function() {
      return this.blogEntries.filter((blogEntry) => {
        return Object
          .values(blogEntry)
          .map(value => {return String(value).toLowerCase()})
          .join()
          .match(this.search)
      });
    }
  }
});
</script>
