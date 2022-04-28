<template>
    <v-card flat>
        <v-card-text>
            <h3>Novo Post</h3>
            <v-form @submit.prevent="save" class="mt-3"  v-model="validation">
                <v-text-field :rules="rule" required label="Título" outlined dense v-model="post.title"></v-text-field>
                <v-text-field :rules="rule" required label="Subtítulo" outlined dense v-model="post.subtitle"></v-text-field>
                <v-textarea :rules="rule" required label="Texto" outlined dense v-model="post.text"></v-textarea>
                <v-text-field label="Inserir Imagem" outlined dense v-model="post.img"></v-text-field>
                <v-card-actions>
                    <perfil-viewsPost :post="post" v-if="validation" />
                    <v-spacer></v-spacer>
                    <v-btn @click="clearFields" color="secondary" outlined>Limpar</v-btn>
                    <v-btn type="submit" color="success lighten-2">Enviar</v-btn>
                </v-card-actions>
            </v-form>
        </v-card-text>
        {{postEdit}}
    </v-card>
</template>

<script>
    import { mapActions } from 'vuex'
    const shortid = require('shortid');

    export default {
        data(){
            return{
                post:{
                    id: null,
                    title: '',
                    subtitle: '',
                    text: '',
                    img: null,
                    show: false,
                    date: null       
                },
                validation: false,
                rule:[
                    v => !!v || 'Campo obrigatório'
                ],
            }
        },
        methods:{
            ...mapActions(['savePost']),
            clearFields(){
                this.post = {
                    title: '',
                    subtitle: '',
                    text: '',
                    img: ''        
                }
            },
            save(){
                if(this.validation){
                    this.post.id = shortid.generate()
                    this.post.img ? this.post.img : this.post.img = '/noImg.png'
                    this.post.date = Date.now()
                    this.savePost(this.post)
                    this.clearFields()
                    // this.$store.dispatch("snackbar/setSnackbars", {text: 'novo post. incluído', color:'primary', timeout:'3000'})
                }else {
                    console.log('nda escrito');
                }
            }
        }
    }
</script>