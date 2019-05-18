<template>
    <div class="about">
        我是个人中心
    </div>
</template>

<script>
export default {
  // 页面切换动画
transition:"transleft",
//   transition(to, from) {
//     if (!from) return 'slide-right'
//     return +to.query.page < +from.query.page ? 'slide-left' : 'slide-right'
//   },
    data(){
        return{

        }
    }
}
</script>

<style lang="stylus">
    .about{
        height 500px
    }
</style>
