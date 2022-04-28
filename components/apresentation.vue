<template>
    <v-card flat align="center" class="border">
        <v-card-text>
            <h3>Autor</h3>
            <v-avatar color="error lighten-2" class="my-1" size="90">
                <v-icon dark size="90">mdi-account</v-icon>
            </v-avatar>
            <h3>João Humberto</h3>
            <p>Auditor Fiscal</p>
        </v-card-text>
        <v-divider class="error mx-5"></v-divider>
        <v-card-text class="text--left">
            <h3>Sobre</h3>
            <p style="text-align: justify; hyphens: auto;">Lorem ipsum dolor sit amet conse
                ctetur adipisicing elit. Ratione iusto deleniti quos excepturi reiciendis pos
                simus molestias, ipsam vitae rem perferendis. Eos amet laboriosam consectetur!
                 Exercitationem perspiciatis neque commodi delectus aperiam.</p>
            <h3>Formação</h3>
            <p style="text-align: justify; hyphens: auto;">Lorem ipsum dolor sit amet conse
                ctetur adipisicing elit. Ratione iusto deleniti quos excepturi reiciendis pos
                simus molestias, ipsam vitae rem perferendis. Eos amet laboriosam consectetur!
                 Exercitationem perspiciatis neque commodi delectus aperiam.</p>
            <h3>Redes Sociais</h3>
            <div class="text--center">
                <v-btn class="mt-2 mx-1" icon v-for="(item, i) in socialMidia" :key="i">
                    <v-icon large>{{item.icon}}</v-icon>
                </v-btn>
            </div>
            <br>
            <div class="mt-3">
                <v-icon small>mdi-email</v-icon> E-mail: juninho.joao@hotmail.com
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
        }
    }
</script>

<style scoped>

.border{
    border: 2px solid rgb(242, 166, 166) ;
}

</style>