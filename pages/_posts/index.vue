<template>
    <v-row>
        <v-col>
            <v-card>
               <v-card-text>
                   <v-img 
                   contain
                   height="400"
                   class="white--text text-center"
                    :src="selectPost.img"
                   >
                    <h1 class="dispaly-1">{{title}}</h1>
                    <p>{{selectPost.subtitle}}</p>
                   </v-img>
                   <div class="d-flex justify-space-between">
                       <div>
                            <small>{{datePost}}</small>
                            <h1 class="dispaly-1">{{title}}</h1>
                            <p class="ml-1">{{selectPost.subtitle}}</p>
                       </div>
                       <div>
                           <v-btn icon @click="favorite = !favorite">
                             <v-icon size="50" :color="favorite ? 'warning' : 'secondary'">mdi-star</v-icon>
                           </v-btn>
                       </div>
                   </div>
                   <v-divider></v-divider>
                   <p>{{selectPost.text}}</p>
               </v-card-text>
               <v-card-actions>
                   <v-icon>mdi-share</v-icon>
                   <v-spacer></v-spacer>
                   <v-btn text color="error">Reportar Erro</v-btn>
               </v-card-actions>
            </v-card>
        </v-col>
    </v-row>
</template>

<script>
    import moment from 'moment'
    export default {
        data(){
            return{
                id: this.$route.query.id,
                title: this.$route.params.posts,
                favorite: false
            }
        },
        computed:{
            posts(){
                return this.$store.getters.readPosts
            },
            selectPost(){
                let post = ''
                
                this.posts.forEach(x => 
                    x.id == this.id ? post = x : ''
                );
                return post
            },
            datePost(){
                moment.locale('pt-br')
                let datepost = moment(this.selectPost.date).format('lll')
                return datepost

            }
        },
    }
</script>
