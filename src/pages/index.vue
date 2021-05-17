<template lang="pug">
  div
    ul(v-for="item in items" :key="item.title" target="_blank" rel="noopener noreferrer" router exact)
      li
        a(:href="item.title") {{ item.title }}
        div {{ item.subtitle }}
    div https://content.nuxtjs.org/ja
    div pug!!
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  data: () => ({
    items: [
      { title: "https://v2.vuetifyjs.com/ja/", subtitle: "vuetifyjs" },
      { title: "https://v2.vuetifyjs.com/ja/", subtitle: "vuetifyjs" }
    ]
  })
});
</script>

<style>
</style>