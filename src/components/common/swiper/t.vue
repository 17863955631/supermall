<template>
  <div id="zzw-swiper">
    <div class="swiper" @touchstart="touchStart" @touchmove="touchMove" @touchend="touchEnd">
      <slot></slot>
    </div>
    <div class="indicator">
      <slot name="indicator" v-if="showIndicator && slideCount>1">
        <div class="indi-item" v-for="(item,index) in slideCount" :class="{active: index===crrentIndex-1}" :key="index"></div>
      </slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'T',
  props: {
    interval: {
      type:Number,
      default: 3000
    },
    animDuration: {
      type: Number,
      default: 300
    },
    moveRatio: {
      type: Number,
      default: 0.25
    },
    showIndicator: {
      type: Boolean,
      default: true
    }
  },
  data() {
    return {
      slideCount: 0,
      totalWidth: 0,
      swiperStyle: {},
      currentIndex: 1,
      scrolling: fasle
    }
  },
  mounted() {

  },
  methods: {
    startTime() {
      this.playTimer = window.setInterval(() => {
        this.currentIndex++;
        this.scrollContent(-this.currentIndex * this.totalWidth)
      }, this.interval)
    },
    stopTimer() {
      window.clearInterval(this.playTimer)
    },
    scrollContent(currentPosition) {
      this.scrolling = true
      this.swiperStyle.transition = `transform ${this.animDuration}ms`
      this.setTransform(currentPosition)
      this.checkPosition()
      this.scrolling = false
    },
    checkPosition() {
      widnow.setTimeout(() => {
        this.swiperStyle.transition = '0ms'
        if(this.currentIndex > tis.slideCount) {
          this.currentIndex = 1
          this.setTransform(-this.currentIndex * this.totalWidth)
        }
        else if(this.currentIndex <= 0) {
          this.currentIndex = this.slideCount
          this.setTransform(-this.currentIndex * this.totalWidth)
        }

        this.$emit('transitionEnd', this.currentIndex-1)
      }, this.animDuration);
      
    },
    setTransform(position) {
      this.swiperStyle.transform = `translate3D(${position}px, 0, 0)`
    },
    handleDom() {
      let swiperEl = document.querySelector('.swiper');
        let slidesEls = swiperEl.getElementsByClassName('slide');
        this.slideCount = slidesEls.length;
        if (this.slideCount > 1) {
          let cloneFirst = slidesEls[0].cloneNode(true);
          let cloneLast = slidesEls[this.slideCount - 1].cloneNode(true);
          swiperEl.insertBefore(cloneLast, slidesEls[0]);
          swiperEl.appendChild(cloneFirst);
          this.totalWidth = swiperEl.offsetWidth;
          this.swiperStyle = swiperEl.style;
        }
        this.setTransform(-this.totalWidth);
    },
    touchStart: function (e) {
        // 1.如果正在滚动, 不可以拖动
        if (this.scrolling) return;

        // 2.停止定时器
        this.stopTimer();

        // 3.保存开始滚动的位置
        this.startX = e.touches[0].pageX;
      },

      touchMove: function (e) {
        // 1.计算出用户拖动的距离
        this.currentX = e.touches[0].pageX;
        this.distance = this.currentX - this.startX;
        let currentPosition = -this.currentIndex * this.totalWidth;
        let moveDistance = this.distance + currentPosition;

        // 2.设置当前的位置
        this.setTransform(moveDistance);
      },

      touchEnd: function (e) {
        let currentMove = Math.abs(this.distance);
        if (this.distance === 0) {
          return
        } else if (this.distance > 0 && currentMove > this.totalWidth * this.moveRatio) { // 右边移动超过0.5
          this.currentIndex--
        } else if (this.distance < 0 && currentMove > this.totalWidth * this.moveRatio) { // 向左移动超过0.5
          this.currentIndex++
        }
        this.scrollContent(-this.currentIndex * this.totalWidth);
        this.startTimer();
      }

  }
}
</script>

<style scoped>

</style>>
