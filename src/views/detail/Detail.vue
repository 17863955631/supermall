<template>
  <div id="detail">
    <detail-nav-bar></detail-nav-bar>
    <button @click="btnClick">按钮</button>
  </div>
</template>

<script>
import Vue from 'vue'
import Toast from "components/common/toast"
Vue.use(Toast)
import DetailNavBar from "./childComps/DetailNavBar"
import {getDetail} from "network/detail"
export default {
  name: 'Detail',
  components: {
    DetailNavBar
  },
  data() {
    return {
      id: null,
    }
  },
  created() {
    this.id = this.$route.params.id
    getDetail(this.id).then(res => {

    })
  },
  methods: {
    btnClick() {
      this.$toast.show("这是详情页")
    }
  }
}
</script>

<style scoped>

</style>