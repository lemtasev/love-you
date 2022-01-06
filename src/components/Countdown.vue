<template>
  <div class="countdown">
    <div class="part">{{ $moment.duration(count).years() }}</div>
    <div class="part">年</div>
    <div class="part">{{ $moment.duration(count).months() }}</div>
    <div class="part">月</div>
    <div class="part">{{ $moment.duration(count).days() }}</div>
    <div class="part">日</div>
    <div class="part">{{ $moment.duration(count).hours() }}</div>
    <div class="part">时</div>
    <div class="part">{{ $moment.duration(count).minutes() }}</div>
    <div class="part">分</div>
    <div class="part">{{ $moment.duration(count).seconds() }}</div>
    <div class="part">秒</div>
  </div>
</template>

<script>
export default {
  name: 'Countdown',
  data () {
    return {
      deadline: new Date('2031-12-09 00:00:00'),
      // deadline: new Date('2022-01-06 12:30:00'),
      interval: null,
      count: 0
    }
  },
  created () {
    console.log(this.$moment()
      .add(9, 'years')
      .add(11, 'months')
      .add(1, 'days')
      .add(6, 'hours')
      .add(53, 'minutes')
      .format('YYYY-MM-DD HH:mm:ss'))
    let now = new Date()
    this.count = this.deadline.getTime() - now.getTime() // 毫秒
    this.interval = setInterval(_ => {
      // console.log(this.count)
      // console.log(this.$moment.duration(count).years(), '年')
      // console.log(this.$moment.duration(count).months(), '月')
      // console.log(this.$moment.duration(count).days(), '日')
      // console.log(this.$moment.duration(count).hours(), '时')
      // console.log(this.$moment.duration(count).minutes(), '分')
      // console.log(this.$moment.duration(count).seconds(), '秒')
      this.count -= 1000
      if (this.count < 0) {
        this.count = 0
        clearInterval(this.interval)
      }
    }, 1000)
  }
}
</script>

<style lang="scss" scoped>
.countdown {
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  border-radius: 4px;
  overflow: hidden;

  .part {
    width: 30px;
    height: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: aliceblue;
  }
}
</style>
