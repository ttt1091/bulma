<template>
  <div>
    <h2>記事一覧</h2>
    <Card v-for="(article, index) in articles" :key="index" :title="article.title" :date="$dateTimeToJaDate(article.updated_at)" :category="article.category" :slug="'/posts/'+ article.slug" :thumbnail="article.thumbnail" />
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const query = await $content('articles').limit(15).sortBy('updated_at', 'desc')
    const articles = await query.fetch()
    return { articles }
  }
}
</script>