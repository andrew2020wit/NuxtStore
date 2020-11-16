<template>
  <article>
    <nuxt-content :document="news" />
    <p>created: {{ formatDate(news.createdAt) }}</p>
    <hr />
    <h3>news-object:</h3>
    <pre> {{ news }} </pre>
  </article>
</template>

<script lang="ts">
import Vue from 'vue';
export default Vue.extend({
  async asyncData({ $content, params }) {
    const news = await $content('news', params.slug).fetch();
    return { news };
  },
  methods: {
    formatDate(date: string | Date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' };
      return new Date(date).toLocaleDateString('en', options);
    },
  },
});
</script>
