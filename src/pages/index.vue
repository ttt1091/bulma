<template>
  <div>
    <ul v-for="item in items" :key="item.title" target="_blank" rel="noopener noreferrer" router exact>
      <li>
        <a :href="item.title">{{ item.title }}</a>
        <div>{{ item.subtitle }}</div>
      </li>
    </ul>
    <div>https://content.nuxtjs.org/ja</div>
    <div>pug!!</div>
  </div>
</template>

<script>
  export default {
  data: () => ({
    items: [
      { title: "https://v2.vuetifyjs.com/ja/", subtitle: "vuetifyjs" },
      { title: "https://v2.vuetifyjs.com/ja/", subtitle: "vuetifyjs" }
    ]
  })
  }
</script>

<style scoped>

</style>