<template>
  <div class="toast" v-show="isShow">
    {{message}}
  </div>
</template>

<script>
export default {
  name: "Toast",
  props: {
    
  },
  data() {
    return {
      isShow: false,
      message: '',
      duration: 0
    }
  },
  methods: {
    show(message="HelloWorld", duration=2000) {
      this.isShow = true
      this.message = message
      this.duration = duration
      setTimeout(() => {
        this.isShow = false
      }, duration)
    }
  }
}
</script>

<style scoped>
  .toast {
    position: fixed;
    top: 50%;
    left: 50%;
    z-index: 999;
    transform: translate(-50%, -50%);
    background-color: rgba(255, 255, 255, 0.7);
  }
</style>