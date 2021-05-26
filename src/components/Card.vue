<template>
  <v-card :to="slug">
    <BreadCrumb :bread-crumbs="breadCrumbs" />
    <article class="border p-4 rounded my-4">
      <h2 class="text-xl font-bold">{{ title }}</h2>
      <time class="text-right text-sm text-gray-700">{{ date }}</time>
      <div class="tags"><Tag class="category-items">{{ category }}</Tag></div>
      <div>
        <v-img
          :src="require('~/assets/images/thumbnails/'+imgPath)"
          aspect-ratio="1"
          width="80px"
        ></v-img>
        {{thumbnail}}
      </div>
    </article>
  </v-card>
</template>

<script>
import BreadCrumb from '~/components/BreadCrumb';
export default {
  components: {
    BreadCrumb,
  },
  props: {
    title: String,
    date: String,
    category: String,
    slug: String,
    thumbnail: String
  },
  data(){
    return {
      imgPath: this.thumbnail
    }
  }
}
</script>

<style>
.category-items{
  padding: 4px 8px;
  font-size: .8rem;
  min-width: 50px;
  text-align: center;
  background-color: #F05E1C;
  color: #FFF;
  border-radius: .25rem;
}
</style>