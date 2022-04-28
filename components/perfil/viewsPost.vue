<template>
    <v-dialog v-model="dialog" max-width="800">
        <template v-slot:activator="{ on, attrs}">
            <v-btn text v-on="on" v-bind="attrs"><v-icon>mdi-card-search-outline</v-icon>pré-visualizar</v-btn>
        </template>
        <v-card>
       <v-app-bar dark flat class="mb-5" color="#4DBCAC">
           Pré-visualização
       </v-app-bar>
       <v-card-text>
           <v-img contain :src="post.img ||'/noImg.png'"></v-img>
           <div>
            <h3 class="display-1">{{post.title}}</h3>
            <p>{{post.subtitle}}</p>
            <p>{{post.text}}</p>
            <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn icon>Ver<v-icon>mdi-plus</v-icon></v-btn>
            </v-card-actions>
           </div>
        </v-card-text>
    </v-card>
    </v-dialog>
</template>

<script>
    export default {
        data(){
            return{
                dialog: false,
            }
        },
        props:{
            post:Object
        }
    }
</script>

<style lang="scss" scoped>

</style>