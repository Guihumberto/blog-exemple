<template>
    <v-tabs-item>
        <v-card tile class="card_item pa-2">
            <v-card-text>
            <h3>Postagens</h3>
            <v-list two-line>
                <v-list-item-group
                v-model="selected"
                active-class="pink--text"
                >
                    <template v-for="(item, i) in posts">
                        <v-list-item :key="i">
                            <v-list-item-avatar>
                                <v-avatar size="70">
                                    <v-img :src="item.img"></v-img>
                                </v-avatar>
                            </v-list-item-avatar>
                            <v-list-item-content>
                                <v-list-item-title>{{item.title}}</v-list-item-title>
                                <v-list-item-subtitle class="text--primary">{{item.subtitle}}</v-list-item-subtitle>
                                <v-list-item-subtitle>{{item.text}}</v-list-item-subtitle>
                            </v-list-item-content>
                            <v-list-item-action>
                                <div>
                                    <v-btn color="primary" small outlined class="mr-1" @click="dialog = true">
                                        <v-icon small>mdi-playlist-edit</v-icon>
                                    </v-btn>
                                    <v-btn @click="deletePost(item.id)" color="error" small outlined><v-icon small>mdi-delete</v-icon></v-btn>
                                    <v-switch label="Publicar" v-model="item.show" dense></v-switch>
                                </div>
                            </v-list-item-action>
                        </v-list-item>
                        <v-divider></v-divider>
                        <v-dialog max-width="800" v-model="dialog">
                            <v-card>
                                <v-app-bar dark flat class="mb-5" color="#4DBCAC">
                                    Editar Post
                                </v-app-bar>
                                <perfil-addPost />
                            </v-card>
                        </v-dialog>
                    </template>
                </v-list-item-group>
            </v-list>
            </v-card-text>
        </v-card>
    </v-tabs-item>
</template>

<script>
    import { mapActions } from 'vuex'
    export default {
        data(){
            return{
                selected: 0,
                dialog: false
            }
        },
        computed:{
            posts(){
                return this.$store.getters.readPosts
            }
        },
        methods:{
            ...mapActions(['deletePost']),
        }
    }
</script>

<style scoped>

</style>