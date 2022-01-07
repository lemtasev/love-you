<template>
  <div class="home">
    <Version/>
    <Countdown/>
  </div>
</template>

<script>
import Version from '@/components/Version'
import Countdown from '@/components/Countdown'

export default {
  name: 'Home',
  components: {
    Version,
    Countdown
  },
  data () {
    return {
      msg: 'TEST'
    }
  }
}
</script>

<style lang="scss" scoped>
.home {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background: #42b983;
}
</style>
