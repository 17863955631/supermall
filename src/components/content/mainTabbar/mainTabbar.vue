<template>
  <div>
    <tab-bar>
      <tab-bar-item path="/home" activeColor="blue">
        <img slot="item-icon" src="~/assets/image/tabbar/Home.png" alt="">
        <img slot="item-icon-active" src="~/assets/image/tabbar/Home.png" alt="">
        <div slot="item-text">首页</div>
      </tab-bar-item>
      <tab-bar-item path="/category" activeColor="green">
        <img slot="item-icon" src="~/assets/image/tabbar/购物车.png" alt="">
        <img slot="item-icon-active" src="~/assets/image/tabbar/购物车.png" alt="">
        <div slot="item-text">分类</div>
      </tab-bar-item>
      <tab-bar-item path="/cart" activeColor="green">
        <img slot="item-icon" src="~/assets/image/tabbar/购物车.png" alt="">
        <img slot="item-icon-active" src="~/assets/image/tabbar/购物车.png" alt="">
        <div slot="item-text">购物车</div>
      </tab-bar-item>
      <tab-bar-item path="/profile">
        <img slot="item-icon" src="~/assets/image/tabbar/我的.png" alt="">
        <img slot="item-icon-active" src="~/assets/image/tabbar/我的.png" alt="">
        <div slot="item-text">我的</div>
      </tab-bar-item>
    </tab-bar>
  </div>
</template>

<script>
  import TabBar from "../../common/tabbar/TabBar"
  import TabBarItem from "../../common/tabbar/TabBarItem"
  export default {
    name: 'MainTabbar',
    components: {
      TabBar,
      TabBarItem
    }
  }
</script>

<style scoped>
  @import "../../../assets/css/base.css";
</style>