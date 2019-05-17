<template>
  <div class="container">
    <!-- 手势 -->
    <!-- 1.npm install vue-touch@next
    2.import Vue from 'vue';
      var VueTouch = require('vue-touch');
      Vue.use(VueTouch, {name: 'v-touch'}); -->
    <!-- 3 <v-touch tag="a"  v-on:swipeleft="sidUp" v-on:swiperight="sidUp"></v-touch>   -->
    <v-touch tag="a"  v-on:swipeleft="sidUp" v-on:swiperight="sidUp"> 
      <p>About Page</p>
      <p>It should take 5 seconds for the loader to disappear</p>
      <p>
        It should take 5 seconds for the route to change after you
          click here
      </p>
      <!-- <nuxt-link to="/">返回</nuxt-link> -->
    </v-touch>
  </div>
</template>

<script>
export default {
  transition(to, from) {
    if (!from) return 'slide-left'
    return +to.query.page < +from.query.page ? 'slide-right' : 'slide-left'
  },
  asyncData() {
    return new Promise((resolve) => {
      setTimeout(function () {
        resolve({})
      })
    })
  },
  mounted() {

  },
  methods: {
    sidUp(){
      console.log("9999999");
      // this.$router.push({path:"/home"});
      this.$router.go(-1);//返回上一层
    }
  }
}
</script>

<style scoped>
.link {
  cursor: pointer;
  text-decoration: underline;
}
.container {
  background: #f00;
  font-size: 20px;
  text-align: center;
  padding-top: 100px;
  cursor: pointer;
}
</style>
