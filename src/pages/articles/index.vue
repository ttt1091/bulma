<template lang="pug">
  .articles-container
    <div class="articles">
      <article class="post-items" v-for="b in articles" :key="b.slug" :to="'/articles/'+ b.slug" nuxt>
        <nuxt-link :to="'/articles/'+ b.slug">{{b.title}} {{b.date}}</nuxt-link>
        <div>{{b.tags}}</div>
      </article>
    </div>
</template>
<script>
export default {
  async asyncData ({ $content, params }) {
    const query = await $content('articles' || 'index', { deep: true }).limit(10).sortBy('updated_at', 'desc')
    const articles = await query.fetch()
    return { articles }
  }
}
</script>
