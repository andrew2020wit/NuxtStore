<template>
  <article>
    <nuxt-content :document="news" />
  </article>
</template>

<script lang="ts">
import Vue from 'vue';
export default Vue.extend({
  async asyncData({ $content, params }) {
    const news = await $content('news', params.slug).fetch();
    return { news };
  },
});
</script>
