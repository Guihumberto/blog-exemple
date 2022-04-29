<template>
    <v-card flat align="center" class="border">
        <v-card-text>
            <h3>Autor</h3>
            <v-avatar color="error lighten-2" class="my-1" size="90">
                <v-icon dark size="90">mdi-account</v-icon>
            </v-avatar>
            <h3>{{author.name}}</h3>
            <p>{{author.job}}</p>
        </v-card-text>
        <v-divider class="error mx-5"></v-divider>
        <v-card-text class="text--left">
            <h3>Sobre</h3>
            <p style="text-align: justify; hyphens: auto;">{{author.about}}.</p>
            <h3>Formação</h3>
            <v-list>
                <v-list-item class="mt-n3" v-for="(item, i) in author.formation" :key="i">
                    <small>{{item}}</small>
                </v-list-item>
            </v-list>
            <div class="text--center">
                <v-btn class="mt-2 mx-1" icon v-for="(item, i) in author.socialmidia" :key="i">
                    <v-icon large>{{item.icon}}</v-icon>
                </v-btn>
            </div>
            <br>
            <div class="mt-3">
                <v-icon small>mdi-email</v-icon> E-mail: {{author.email}}
            </div>
        </v-card-text>
    </v-card>
</template>

<script>
    export default {
        data(){
            return{
                socialMidia:[
                    {icon: 'mdi-whatsapp', url:''},
                    {icon: 'mdi-facebook', url:''},
                    {icon: 'mdi-instagram', url:''},
                    {icon: 'mdi-linkedin', url:''},
                ]
            }
        },
        computed:{
            author(){
                return this.$store.getters.readAuthor
            }
        }
    }
</script>

<style scoped>

.border{
    border: 2px solid rgb(242, 166, 166) ;
}

</style>