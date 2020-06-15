<template>
  <ul>
    <li v-for="n in articles" :key="n.slug">
      <nuxt-link :to="`/${n.slug}`">{{ n.title }} {{ n.date }}</nuxt-link>
    </li>
  </ul>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  async asyncData ({ $content, params }) {
    const query = await $content('articles' || 'index').limit(15)
    const articles = await query.fetch()
    return { articles }
  }
})
</script>
