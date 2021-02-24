<template>
  <div>
    <h1>{{id}}</h1>
  </div>
</template>

<script>

export default {
  data () {
    return {
      id: null
    }
  },
  created: function () {
    this.id = this.$route.params.id
  },
  beforeRouteLeave (to, from, next) {
    console.log(to)
    to.meta.keepAlive = true
    next()
  }
}
</script>

<style>

</style>
