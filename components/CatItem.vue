<template>
  <div>
    <v-row>
      <v-col
        cols="12"
        sm="12"
        md="12"
        lg="6"
        xl="6"
        :class="$style.cats"
        v-for="cat in cats"
        :key="cat.uuid"
      >
        <div>
          <img :src="cat.url" :alt="cat.uuid" :class="$style.cats_image" />
          <div>撮影場所：{{ cat.address }}</div>
          <div>撮影日：{{ cat.createDate | moment }}</div>
        </div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  props: {
    cats: {
      type: Array,
      default: () => [],
    },
  },
}
</script>

<style lang="scss" module>
.cats {
  margin-bottom: 16px;
  padding-bottom: 16px;
  border-bottom: 2px solid #ccc;
  width: 1000px;
}
.cats_image {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}
</style>
