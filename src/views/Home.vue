<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
        <List/>
  </div>
</template>

<script>
// @ is an alias to /src
import List from '@/components/List.vue'

export default {
  name: 'Home',
  components: {
    List
  },
  beforeRouteLeave (to, from, next) {
    from.meta.keepAlive = true
    next()
  }
}
</script>
