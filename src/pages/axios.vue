<template>
  <div>
    <h2>title</h2>
    <ul>
      <li
        v-for="(axiositem, axiosi) in axiosdata"
        :key="axiosi"
        class="axitems"
      >
        id:{{ axiositem.id }} / name:{{ axiositem.name }} / ruby:{{axiositem.ruby}} / bust:{{axiositem.bust}} / <br>
        cup:{{axiositem.cup}} / waist:{{axiositem.waist}} / hip:{{axiositem.hip}} / height:{{axiositem.height}} / <br>
        birthday:{{axiositem.birthday}} / blood_type:{{axiositem.blood_type}} / hobby:{{axiositem.hobby}} / prefectures:{{axiositem.prefectures}} / <br>
        imageURL:{{axiositem.imageURL}} / <br><br>
        <div v-if="!axiositem.imageURL">
          none
        </div>
        <div v-else-if="!axiositem.imageURL.large">
          noneLarge
        </div>
        <div v-else>
          <img :src="axiositem.imageURL.small" alt="" width="30px">
          <img :src="axiositem.imageURL.large" alt="" width="30px">
        </div>
        <br>
        listURL:{{axiositem.listURL}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return{
      data: "",
      axiosdata: ""
    }
  },
  async asyncData({ $axios }) {
    const response = await $axios.$get("https://api.dmm.com/affiliate/v3/ActressSearch?api_id=cxM3V1cGvP7qBxKNpdB6&affiliate_id=eroninja-990&keyword=&gte_bust=&lte_waist=&sort=id&hits=100&offset=50000&output=json")
      .catch( error => {
        console.log("response error", error)
        return false
      })
    return { axiosdata: response.result.actress }
  },
}
</script>

<style scoped>
.axitems{
  border: solid 1px #ddd;
  margin: 8px;
  padding: 8px;
}
</style>
