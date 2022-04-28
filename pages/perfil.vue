<template>
    <v-row>
        <v-col cols="12">
            <div class="mb-3">
                <h3 class="display-1">Administração</h3>
                <p class="mb-0">Perfil e edição do blog</p>
            </div>
            <v-container>
                <v-app-bar flat>
                    <v-tabs v-model="tab"> 
                        <v-tab>Inserir</v-tab>
                        <v-tab>Posts</v-tab>
                        <v-tab>Perfil</v-tab>
                    </v-tabs>
                </v-app-bar>
                <v-card tile class="my-2" min-height="500">
                    <v-row>
                        <v-col>
                            <v-tabs-items v-model="tab">
                                <v-tab-item>
                                    <perfil-addPost />
                                </v-tab-item>
                                <v-tab-item>
                                    <perfil-listPosts />
                                </v-tab-item>
                                <v-tab-item>
                                    <perfil-user />
                                </v-tab-item>
                            </v-tabs-items>
                        </v-col>
                    </v-row>          
                </v-card>
            </v-container>
        </v-col>
    </v-row>
</template>

<script>
    export default {
        data(){
            return{
                tab: null
            }
        }
    }
</script>

