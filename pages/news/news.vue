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


