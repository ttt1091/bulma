<template>
  <article>
    <v-card
      class="mx-auto"
    >
      <v-img
        class="white--text align-end"
        max-height="400px"
        :src="require('@/assets/images/thumbnails/'+article.thumbnail)"
      >
        <v-card-title><h1 class="">{{ article.title || '' }}</h1></v-card-title>
      </v-img>

      <v-card-subtitle class="pb-0">{{$dateTimeToJaDate(article.updated_at)}}</v-card-subtitle>

      <v-card-text class="text--primary">
        <nuxt-content :document="article" />
      </v-card-text>
    </v-card>
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const query = $content('articles', params.slug)
    const article = await query.fetch()
    return { article }
  },
  data () {
    return {
    }
  }
}
</script>

<style>
.v-card__title{
  background: #FFF;
  color: #444;
  font-size: 1rem;
  margin: 0 16px -16px 16px;
  border-radius: 0.35rem;
  padding: 8px;
}
</style>