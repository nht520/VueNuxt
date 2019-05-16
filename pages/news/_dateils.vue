<template>
    <div>
        <p>{{dateils.mealContent}}</p>
        <p>{{dateils.mealName}}</p>
    </div>
</template>
<script>
    import Axios from 'axios';
    export default {
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


