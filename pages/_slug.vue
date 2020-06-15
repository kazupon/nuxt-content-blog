<template>
  <article>
    <h1>{{ article.title }}</h1>
    <p>createdAt: {{ article.createdAt }}</p>
    <p>updatedAt: {{ article.updatedAt }}</p>
    <div v-for="tag in article.tags" :key="tag">{{ tag }}</div>

    <nuxt-content :document="article" />
  </article>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  async asyncData ({ $content, params }) {
    const article = await $content('articles', params.slug || 'index').fetch()
    console.log('slug', article)
    return { article }
  }
})
</script>
