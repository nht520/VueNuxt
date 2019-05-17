<template>
    <div>
        <p>{{dateils.mealContent}}</p>
        <p>{{dateils.mealName}}</p>
        <nuxt-link to="/">返回</nuxt-link>
    </div>
</template>
<script>
    import Axios from 'axios';
    export default {
          // Called to know which transition to apply
        transition(to, from) {
            if (!from) return 'slide-left'
            return +to.query.page < +from.query.page ? 'slide-right' : 'slide-left'
        },
        data(){
            return{
                dateils:[]
            }
        },
        methods:{
            details(){
                this.detlsid = this.$route.params.id;
                const date={
                    params:{
                        id:1,
                    }
                };
                const api = window.g.mealDts;
                Axios.get(api,date).then((res)=>{
                    console.log(res)
                    this.dateils=res.data.data;
                }).catch((err)=>{
                    console.log(err)
                })
            }
        },
        mounted() {
          console.log(this.$route.params.id);
          this.details();
        }   
    }
</script>
<style lang="stylus" scoped>

</style>


