<template>
  <div id="container">
      <h1>999999999</h1>
        <nuxt-link to="/home">home</nuxt-link>
        <nuxt-link to="/login">login</nuxt-link>      
      <ul>
        <li v-for=" item in list "  :key="item.id">
          <h1>{{item.mealContent}}</h1>
          <p>{{item.mealDetail}}</p>
          <p>{{item.first_name}}</p>
          <img :src="item.avatar"/>
        </li>
      </ul>
      <el-button type="primary" @click="submit()">主要按钮</el-button>
      <!-- 新闻 -->
      <news></news>
      <!-- 嵌套路由  
        普通路由 /parent/
        默认路由 /parent/class
      -->
      <nuxt-link to="/parent/class">嵌套路由</nuxt-link> 
      <!-- 引用组件传值 -->
      <Header  :headTitle="msg" ></Header>
  </div>
</template>
<script>
import Axios from 'axios'
import storage from '~/plugins/storage.js'
import news from '~/pages/news/news.vue';
import parent from '~/pages/parent.vue';
import Header from '~/components/Header.vue';
export default {
  // 页面切换动画
  transition(to, from) {
    if (!from) return 'slide-right'
    return +to.query.page < +from.query.page ? 'slide-left' : 'slide-right'
  },
  // 加载动画
  asyncData() {
    return new Promise((resolve) => {
      setTimeout(function () {
        resolve({})
      },500)
    })
  },
  components: {
    news,parent,Header
  },
  data () {
    return{
      msg:"我是首页的头部",
      list:[],
    }
  },
  methods:{
    submit(){
      const api = "https://reqres.in/api/users?page=1";
      Axios.get(api).then((res)=>{
         // Start loader immediately
          // Start loader immediately
          this.$nuxt.$loading.start()
          // Actually change route 5s later
          setTimeout(() => {
            this.$router.push('/home')
          }, 1000)
        // Actually change route 5s later
        this.list=res.data.data;
        storage.set("list",this.list);
      }).catch((err)=>{
        console.log(err)
      })
    }
  },
  mounted() {
  },
}
</script>
<style lang="stylus" scope>
  #container
   text-align center
   width 100%
  #container h1
    color #ff0000 
  #container img
   width 50px
   height 50px  
</style>

