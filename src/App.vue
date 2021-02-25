<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>|
      <router-link :to="{path:'/list/1',params:{id:1}}">List1</router-link>
      <router-link :to="{path:'/list/2',params:{id:2}}">List2</router-link>
    </div>
    <!-- <keep-alive>
      <router-view></router-view>
    </keep-alive> -->
    <keep-alive>
      <router-view :key='$route.fullPath' v-if="$route.meta.keepAlive"></router-view>
    </keep-alive>
      <router-view :key='$route.fullPath' v-if="!$route.meta.keepAlive"></router-view>
      <!-- <router-view :key='$route.fullPath'></router-view> -->
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
