<template>
  <div ref="wrapper">
    <div>
      <slot></slot>
    </div>
  </div>
</template>

<script>
import BScroll from "better-scroll"
export default {
  name: "scroll",
  data() {
    return {
      scroll: null
    }
  },
  props: {
    probeType: {
      type: Number,
      default: 0
    },
    pullUpLoad: {
      type: Boolean,
      default: false
    }
  },
  mounted() {
    this.scroll = new BScroll(this.$refs.wrapper,{
      probeType: this.probeType,
      click: true,
      pullUpLoad: this.pullUpLoad
    })
    this.scroll.on('scroll', (position) => {
      this.$emit('scroll', position)
    })
    this.scroll.on('pullingUp', () => {
      this.$emit('pullingUp')
    })
  },
  methods: {
    finidshPullUp() {
      this.scroll.finidshPullUp()
    }
  }
}
</script>

<style scoped>

</style>