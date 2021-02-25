!<template>
  <div>
    <h1>{{$route.params.id}}</h1>
    <ul>
      <li v-for="item in list" :key="item.id" @click="handleClick(item.id)">
        <div>{{ item.title }}</div>
      </li>
    </ul>
  </div>
</template>

<script>
import Services from '../services/service'

export default {

  created () {
    const params = this.$route.params
    Services.getList(params.id).then(({ data }) => {
      this.list = data
    })
  },
  activated () {
    console.log('s')
  },
  data () {
    return {
      list: []
    }
  },
  methods: {
    handleClick (id) {
      this.$router.push({ name: 'Spec', params: { id } })
    }
  }
}
</script>

<style scoped>
.title {
  text-align: center;
}
ul{
  list-style-type: none;
}
ul li{
  color: rgba(0,0,0,0.65);
  margin-top: 20px;
  padding: 20px 10px;
  border: 1px solid black;
  cursor: pointer;
}
ul li:hover{
  color: rgba(0,0,0,0.85);
  background: rgba(0,0,0,0.4);
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);;
}
</style>
