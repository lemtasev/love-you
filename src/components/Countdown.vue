<template>
  <div class="countdown">
    <div class="part">{{ duration.years() }}</div>
    <div class="part">年</div>
    <div class="part">{{ duration.months() }}</div>
    <div class="part">月</div>
    <div class="part">{{ duration.days() }}</div>
    <div class="part">日</div>
    <div class="part">{{ duration.hours() }}</div>
    <div class="part">时</div>
    <div class="part">{{ duration.minutes() }}</div>
    <div class="part">分</div>
    <div class="part">{{ duration.seconds() }}</div>
    <div class="part">秒</div>
  </div>
</template>

<script>
export default {
  name: 'Countdown',
  data () {
    return {
      deadline: new Date('2031-12-09 12:00:00'),
      // deadline: new Date('2022-03-09 12:00:00'),
      // deadline: new Date('2022-01-08 12:30:00'),
      interval: null,
      count: 0,
      duration: this.$moment.duration(this.count)
    }
  },
  created () {
    let now = new Date()
    this.count = this.deadline.getTime() - now.getTime() // 毫秒
    this.counter()
    this.interval = setInterval(_ => {
      this.counter()
    }, 1000)
  },
  methods: {
    counter () {
      this.count -= 1000
      this.duration = this.$moment.duration(this.count)
      if (this.count < 0) {
        this.count = 0
        clearInterval(this.interval)
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.countdown {
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  border-radius: 1vw;
  overflow: hidden;
  font-size: 4vw;

  .part {
    width: 8vw;
    height: 8vw;
    display: flex;
    align-items: center;
    justify-content: center;
    background: aliceblue;
  }
}
</style>
