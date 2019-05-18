<template>
    <div class="class">
        <p>
            我是分类
        </p>
        <nuxt-link to="/">login</nuxt-link>    
    </div>
</template>

<script>
export default {
    transition:"transleft",
  // 页面切换动画
}
</script>

<style lang="stylus">
    .class{
        height 500px
    }
</style>
