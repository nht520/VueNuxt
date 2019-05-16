<template>
  <div id="container">
    <h1>999999999</h1>
       <nuxt-link to="/home">home</nuxt-link>
        <nuxt-link to="/login">login</nuxt-link>      
    <ul>
      <li v-for=" item in list "  :key="item.id">
        <h1>{{item.mealContent}}</h1>
        <p>{{item.mealDetail}}</p>
        <p>{{item.mealName}}</p>
        <img :src="item.mealImage"/>
      </li>
    </ul>
    <el-button type="primary">主要按钮</el-button>
  </div>
</template>

<script>
import Axios from 'axios'
import storage from '~/plugins/storage.js'
export default {
  transition(to, from) {
    if (!from) return 'slide-left'
    return +to.query.page < +from.query.page ? 'slide-right' : 'slide-left'
  },
  asyncData() {
    return new Promise((resolve) => {
      setTimeout(function () {
        resolve({})
      }, 1000)
    })
  },
  components: {
  },
  data () {
    return{
      list:[]
    }
  },
  methods:{
    submit(){
      const api = "https://reqres.in/api/users?page=1";
      Axios.get(api).then((res)=>{
        console.log(res)
        this.list=res.data.records;
        storage.set("list",this.list);
      }).catch((err)=>{
        console.log(err)
      })
    }
  },
  mounted() {
    this.submit();
  },
}
</script>
<style lang="stylus" scope>
  #container h1
    color #ff0000 
  #container img
   width 50px
   height 50px  
</style>

