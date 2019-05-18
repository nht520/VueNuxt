<template>
    <div class="about">
        <p>
            我是个人中心
        </p>
    </div>
</template>

<script>
export default {
    transition:"transleft",
  // 页面切换动画
//   transition(to, from) {
//     if (!from) return 'slide-right'
//     return +to.query.page < +from.query.page ? 'slide-left' : 'slide-right'
//   },
}
</script>

<style lang="stylus">
    .about{
        height 500px
    }
</style>
