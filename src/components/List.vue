<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <ul>
      <li
      v-for="item in list"
      :key="item.id"
      @click="handleClick(item.id)"
      >
        <div>{{ item.title }}</div>
      </li>
    </ul>
  </div>
</template>

<script>
import Services from '../services/service'

export default {
  created () {
    console.log('list created on')
    Services.getList().then(({ data }) => {
      this.list = data
    })
  },
  data () {
    return {
      list: []
    }
  },
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods: {
    handleClick (id) {
      this.$router.push({ name: 'Spec', params: { id } })
    }
  }
}
</script>

<style scoped>
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
