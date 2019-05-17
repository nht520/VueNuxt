<template>
    <div>
        我是新闻组件
        <ul>
            <li v-for=" item in list" :key="item.id">
                <nuxt-link :to="'/news/dateils/'+item.id">
                    {{item.mealContent}}
                </nuxt-link>
            </li>
        </ul>
    </div>
</template>
<script>
    import Axios from 'axios'
    export default {
          // Called to know which transition to apply
        transition(to, from) {
            if (!from) return 'slide-left'
            return +to.query.page < +from.query.page ? 'slide-right' : 'slide-left'
        },
        data(){
            return{
                list:[],
            }
        },
        methods:{
            news(){
                const api = window.g.meal;
                Axios.get(api).then((res)=>{
                    console.log(res);
                    this.list=res.data.records;
                }).catch((err)=>{
                    console.log(err)
                })
            }
        },
        mounted(){
            this.news();
        }
    }
</script>
<style lang="stylus" scoped>

</style>


