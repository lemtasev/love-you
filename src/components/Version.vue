<template>
  <div class="version">
    <span>ver {{ ver }}</span>
  </div>
</template>

<script>
export default {
  name: 'Version',
  data () {
    return {
      ver: process.env.VERSION
    }
  }
}
</script>

<style lang="scss" scoped>
.version {
  position: fixed;
  bottom: 2px;
  right: 2px;
}
</style>
