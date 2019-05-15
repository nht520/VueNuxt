<template>
    <div>
        我是首页
        <nuxt-link to="/">返回</nuxt-link>
    </div>
</template>
<script>
export default {
    asyncData() {
        return new Promise((resolve) => {
        setTimeout(function () {
            resolve({})
        }, 1000)
        })
    },
    data(){
        return{
            title:""
        }
    },
    methods : {
        
    },
    mounted(){
       document.title="88888888888"
    }
}
</script>
<style lang="stylus" scoped>

</style>


