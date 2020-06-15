<template>
  <article>
    <h1>{{ articles.title }}</h1>
    <dl>
      <dt>date</dt>
      <dd>{{ articles.date }}</dd>
    </dl>
    <div v-for="tag in articles.tags" :key="tag">{{ tag }}</div>

    <nuxt-content :document="articles" />
  </article>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  async asyncData ({ $content, params }) {
    const articles = await $content('articles', params.slug || 'index').fetch()
    return { articles }
  }
})
</script>
