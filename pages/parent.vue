<template>
     <div>
        <!-- 引用组件传值 -->
        <Header  :headTitle="msg" ></Header>
        <!-- <p>我是parent</p> -->
        <!-- sc快速生成命令 -->
        <!-- <ul>
            <li>
                <nuxt-link to="/parent/class">classs</nuxt-link>
            </li>
            <li>
                <nuxt-link to="/parent/about">about</nuxt-link>
            </li>
        </ul> -->
        <nuxt-child></nuxt-child>
        <Navigation></Navigation>
    </div>
</template>
<script>
    import Navigation from '~/components/Navigation.vue';
    export default {
          // 页面切换动画
        transition(to, from) {
            if (!from) return 'slide-right'
            return +to.query.page < +from.query.page ? 'slide-left' : 'slide-right'
        },
        name:"parent",
        components:{
            Navigation
        },
        data(){
            return{
                msg:"首页",
            }
        }
    }
</script>

<style>

</style>
