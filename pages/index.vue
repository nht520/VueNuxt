<template>
  <div id="index">
    <h1>999999999</h1>
    <Loading></Loading>
    <nuxt-link to="/home">home</nuxt-link>
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
import Loading from '~/components/Loading.vue'
export default {
  asyncData() {
    return new Promise((resolve) => {
      setTimeout(function () {
        resolve({})
      }, 1000)
    })
  },
  components: {
    Loading
  },
  data () {
    return{
      list:[]
    }
  },
  methods:{
    submit(){
      const api = window.g.meal;
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
  #index h1
    color #ff0000 
  #index img
   width 50px
   height 50px  
</style>

