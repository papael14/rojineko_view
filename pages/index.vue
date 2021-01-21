<template>
  <div>
    <cat-item :cats="cats" />
  </div>
</template>

<script>
// import ImageUtil from '../lib/imageUtil'
import CatItem from '@/components/CatItem.vue'

export default {
  components: {
    CatItem,
  },
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
      this.cats = response.data.results
      // for (let i = 0; i < 11; i++) {
      //   this.cats[i].url = await ImageUtil.getCompressImageFileAsync(
      //     this.cats[i].url
      //   )
      // }
    } catch (err) {
      const res = err.response
      alert(res)
    }
  },
}
</script>
