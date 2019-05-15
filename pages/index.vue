<template>
  <div id="index">
    <h1>999999999</h1>
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
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'
import Axios from 'axios'
import storage from '~/plugins/storage.js'
export default {
  components: {
    Logo,
    VuetifyLogo
  },
  data () {
    return{
      list:[]
    }
  },
  methods:{
    submit(){
      const api = "http://wx.bomao.xyz:8080/distributor/distributor/meal";
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
<style lang="stylus" scoped>
  & h1
    color #ff0000 
  #index img
   width 50px
   height 50px  
</style>

