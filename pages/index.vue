<template>
  <v-row justify="center" align="center">
    <v-col>
      <!-- title -->
      <div class="mb-3">
        <h3 class="display-1 grey--text"> <v-icon size="40" color="warning">mdi-star</v-icon> Rock Star</h3>
        <p class="mb-0 ml-2 caption">If the sun refused to shine
          I would still be loving you
          When mountains crumble to the sea
          There will still be you and me
        </p>
        <small>{{dataAtual}}</small>
      </div>
      <!--banner  -->
      <v-card align="center" color="primary lighten-1">
        <v-img
          max-height="500"
          src="/led.png"
        ></v-img>
      </v-card>

      <!-- text img -->
      <v-card flat>
        <v-card-text>
          <h3 class="display-1">Led Zeppelin</h3>
          <p class="ml-1">To be to rock and not roll</p>
          <v-btn outlined text>Ler mais</v-btn> <v-btn icon><v-icon>mdi-share-variant</v-icon></v-btn>
        </v-card-text>
      </v-card>

      <!-- Primeiro Posts -->
      <v-card dark flat class="mb-2 border" v-for="(item, i) in postsSelected" :key="i"  color="cyan lighten-2">
        <v-row class="px-5">
          <v-col cols="12" sm="12" md="2" class="mr-n6">
            <v-avatar
                class="ma-3"
                size="125"
                tile
              >
                <v-img class="borderImg" :src="item.img"></v-img>
              </v-avatar>
          </v-col>
          <v-col cols="12" sm="12" md="9" class="ml-n5">
            <v-card-text>
              <h3 class="display-1">{{item.title}}</h3>
              <small>{{dateBr(item.date)}}</small>
              <p>{{item.subtitle}}</p>
              <p class="my-0">{{item.text | truncate(80)}}</p>
            </v-card-text>
          </v-col>
          <v-col cols="12" sm="12" md="1" class="align-self-end ml-auto">
            <v-card-actions>
                <v-icon small>mdi-share-variant</v-icon>
                <v-hover v-slot="{hover}">
                  <v-btn small text :to="{
                          name: 'posts',
                          params:{posts: item.title},
                          query:{id:item.id}  
                        }">
                    Ler<v-icon color="error lighten-1" v-text="hover ? 'mdi-plus' : 'mdi-plus-circle'"></v-icon>
                  </v-btn>
                </v-hover>
              </v-card-actions>
          </v-col>
        </v-row>
      </v-card>

      <!-- segundo posts -->
      <v-row class="mt-5">
        <v-col cols="6" sm="4" v-for="(item, i) in posts" :key="i">
          <h3 class="mb-n2 font-weight-regular">{{item.title}}</h3>
          <small class="grey--text font-italic">{{dateBr(item.date)}}</small>
          <v-card hover class="mb-5">
            <v-img
              height="200"
              :src="item.img"></v-img>
            <v-card-text class="grey lighten-4">
              <h3>{{item.subtitle}}</h3>
              <p>{{item.text | truncate(80)}}</p>
            </v-card-text>
            <v-card-actions class="mb-n3 error lighten-2">
              <v-spacer></v-spacer>
              <v-icon class="mr-2">mdi-share-variant</v-icon>
              <v-hover v-slot="{hover}">
                <v-btn :color="hover ? 'error' : 'white'" small :to="{
                        name: 'posts',
                        params:{posts: item.title},
                        query:{id:item.id}  
                      }">Ler
                  <v-icon :color="hover ? 'white' : 'error lighten-1'">mdi-plus-circle</v-icon>
                </v-btn>
              </v-hover>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>

      <!-- newsletter -->
      <v-card class="mt-3" color="cyan lighten-2">
        <v-card-text>
          <h3 class=" display-1 text--white mb-0">Newsletter <v-icon dark>mdi-email-fast</v-icon></h3>
          <p class="text--white">Inscreva-se no nosso newsletter para receber novidades na caixa de e-mail. </p>
          <v-form class="d-flex">
            <v-text-field outlined solo dense label="E-mail"></v-text-field>
            <v-btn color="error lighten-2" class="ml-5 mt-1">Inscrever</v-btn>
          </v-form>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import moment from 'moment'

export default {
  name: 'IndexPage',
  data(){
    return{
      textDescription:'Lorem ipsum dolor sit amet consectetur adipisicing elit. Maxime, eveniet. Atque numquam a sed distinctio accusamus ab dicta odio saepe dolorem! Modi omnis eveniet recusandae soluta sint asperiores explicabo tenetur.'
    }
  },
  computed:{
    dataAtual(){
      moment.locale('pt-br')
      const hoje = moment(Date.now()).format('lll')
      return hoje
    },
    posts(){
      return this.$store.getters.readPosts
    },
    postsSelected(){
      return this.posts.slice(0, 2)
    }
  },
  methods:{
    dateBr(date){
      moment.locale('pt-br')
      const hoje = moment(date).format('lll')
      return hoje
    }
  }
}
</script>

<style scoped>
.border{
  border: 2px solid rgb(40, 180, 226)
}
.borderImg{
  border: 1px solid rgb(108, 107, 107);
  border-radius: 8px;
}
</style>
