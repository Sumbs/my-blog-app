<template>
  <q-item clickable tag="a" :to="{ name: 'blogEntry', params: { id } }">
    <q-item-section>
      <q-item-label lines="1">
        <span class="text-weight-bold">{{ title }}</span>
      </q-item-label>
      <q-item-label>{{ author }}</q-item-label>
      <q-item-label caption lines="2">{{ content }}</q-item-label>
    </q-item-section>
    <q-item-section side top>
      <q-item-label>{{ createdDate() }}</q-item-label>
    </q-item-section>
  </q-item>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "BlogEntry",
  props: {
    title: {
      type: String,
      required: true,
    },

    year: {
      type: Number,
      default: 1900,
    },

    month: {
      type: Number,
      default: 0,
    },
    day: {
      type: Number,
      default: 1,
    },

    content: {
      type: String,
      default: "",
    },

    author: {
      type: String,
      required: true,
    },

    id: {
      type: Number,
      default: 0,
    },
  },
  methods: {
    createdDate() {
      return new Date(this.year, this.month, this.day)
        .toISOString()
        .substring(0, 10);
    },
  },
  setup() {
    return {};
  },
});
</script>
