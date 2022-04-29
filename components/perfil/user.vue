<template>
    <v-tabs-item>
        <v-card flat class="card_item pa-2">
            <v-card-text>
                <div class="d-flex justify-space-between">
                    <h3 class="mb-5">Perfil</h3>
                    <v-btn outlined small text> <v-icon class="mr-2">mdi-account-edit-outline</v-icon> Editar</v-btn>
                </div>
                <v-row v-for="(item, i) in perfil" :key="i">
                    <v-col cols="2">
                        {{item.title}}
                    </v-col>
                    <v-col cols="10">
                        <span v-if="item.response">{{item.response}}</span>
                        <span v-if="item.formation">
                            <v-list>
                                <v-list-item v-for="(i, index) in item.formation" :key="index">
                                    {{i}}
                                </v-list-item>
                            </v-list>
                        </span>
                        <span v-if="item.socialmidia">
                            <div class="d-flex" >
                                <v-btn icon class="mr-2" v-for="(social, ite) in item.socialmidia" :key="ite">
                                    <v-icon>{{social.icon}}</v-icon>
                                    </v-btn>
                            </div>
                        </span>
                    </v-col>
                </v-row>
            </v-card-text>
        </v-card>
    </v-tabs-item>
</template>

<script>
    export default {
        data(){
            return{

            }
        },
        computed:{
            perfil(){
                return this.$store.getters.readPerfil
            }
        }
    }
</script>

<style scoped>

</style>