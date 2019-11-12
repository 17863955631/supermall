<template>
  <div id="app">
    <keep-alive exclude="Detail"><router-view/></keep-alive>
    <main-tabbar></main-tabbar>
  </div>
</template>

<script>
  import MainTabbar from './components/content/mainTabbar/mainTabbar.vue'
  export default {
    name: 'app',
    components: {
      MainTabbar
    }
  }
</script>

<style>

</style>
