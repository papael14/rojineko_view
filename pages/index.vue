<template>
  <div>
    <div :class="$style.cats" v-for="cat in cats" :key="cat">
      <div>ねこ：{{ cat.url }}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cats: [],
    }
  },
  async created() {
    try {
      const response = await this.$axios.get(
        'https://jsondata.okiba.me/v1/json/7lV2J201227155106'
      )
      // console.log(response)
      this.cats = response.data.results
    } catch (err) {
      const res = err.response
      // console.log(res)
      alert(res)
    }
  },
}
</script>

<style lang="scss" module>
.cats {
  margin: 10px 0;
  padding: 8px;
  border: 2px solid #ccc;
  border-radius: 4px;
}
</style>
