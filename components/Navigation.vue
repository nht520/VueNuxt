<template>
    <div class="Navigation">
        <v-card>
            <v-bottom-nav
                :active.sync="bottomNav"
                :color="color"
                :value="true"
                fixed
                dark
                shift
                >
                <nuxt-link v-for="(item, index) in list " :to="item.path" tag="li" class="bottom">
                    <v-btn dark  :key="index">
                        <span>{{item.title}}</span>
                        <v-icon>{{item.icon}}</v-icon>
                    </v-btn>
                </nuxt-link>
            </v-bottom-nav>
        </v-card>
    </div>
</template>
<script>
export default {
    name:"Navigation",
    data(){
        return{
             bottomNav: 0,
             list:[
                 {
                     title:"video",
                     icon:"music_note",
                     path:"/parent/class"
                 },
                {
                     title:"about",
                     icon:"book",
                     path:"/parent/about"
                 },
                {
                     title:"video",
                     icon:"ondemand_video",
                     path:"/home"
                 },
                {
                     title:"video",
                     icon:"image",
                     path:"/home"
                 }
             ]
        }
    },
    methods:{

    },
    mounted(){

    },
    computed:{
      color () {
        switch (this.bottomNav) {
          case 0: return 'blue'
          case 1: return 'red'
          case 2: return 'brown'
          case 3: return 'indigo'
        }
      }
    }
}
</script>
<style lang="stylus">
    .bottom
     list-style none
    
</style>
