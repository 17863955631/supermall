<template>
  <div class="goods-item">
    <img :src="goodsItem.show.img" alt="" @load="itemImageLoad" @click="itemClick">
    <div>
      <p>{{goodsItem.title}}</p>
      <span class="price">{{goodsItem.price}}</span>
      <span class="collect">{{goodsItem.cfav}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'GoodsListItem',
  props: {
    goodsItem: {
      type: Object,
      default() {
        return {}
      }
    }
  },
  methods: {
    itemImageLoad() {
      this.$bus.$emit('itemImageLoad')
    },
    itemClick() {
      this.$router.push(`/detail${this.goodsItem.iid}`)
    }
  }
}
</script>

<style scoped>

</style>