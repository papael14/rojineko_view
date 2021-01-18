<template>
  <div>
    <div :class="$style.cats" v-for="cat in cats" :key="cat.uuid">
      <div>
        <img v-bind:src="cat.url" alt="cat.uuid" :class="$style.cats_image" />
      </div>
      <div>撮影場所：{{ cat.address }}</div>
      <div>撮影日：{{ cat.createDate | moment }}</div>
    </div>
  </div>
</template>

<script>
import ImageUtil from '../lib/imageUtil'
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
      for (let i = 0; i < 11; i++) {
        this.cats[i].url = await ImageUtil.getCompressImageFileAsync(
          this.cats[i].url
        )
      }
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
  margin-bottom: 16px;
  padding-bottom: 16px;
  border-bottom: 2px solid #ccc;
  width: 1000px;
  // border-radius: 4px;
}
.cats_image {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}
</style>
