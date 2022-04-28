<template>
  <v-app>
    <v-app-bar
      fixed
      app
      flat
      color="#4DBCAC"
      dark
    >
    <v-container style="width:1080px;" class="d-flex justify-space-between">
      <nuxt-link class="nuxt-link mt-2" to="/">
        <v-toolbar-title><v-icon class="mr-2">mdi-notebook</v-icon>{{title}} </v-toolbar-title>
      </nuxt-link>
      <div>
        <v-btn icon><v-icon>mdi-magnify</v-icon></v-btn>
        <v-btn icon><v-icon>mdi-bell</v-icon></v-btn>
        <v-btn icon><v-icon large>mdi-instagram</v-icon></v-btn>
      </div>
    </v-container>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-row>
          <v-col cols="12" sm="12" md="2">
          </v-col>
          <v-col cols="12" sm="12" md="8">
            <v-container style="max-width:1080px">
              <Nuxt />
            </v-container>
          </v-col>
          <v-col cols="12" sm="12" md="2">
            <apresentation />
          </v-col>
        </v-row>
      </v-container>
    </v-main>
    <v-footer
      color="#4DBCAC"
      :absolute="!fixed"
      app
    >
    <v-card
        flat
        tile
        color="#4DBCAC"
        width="100%"
        class="text-center"
        dark
      >
        <v-card-text>
          <v-btn
            v-for="icon in icons"
            :key="icon"
            class="mx-4"
            icon
          >
            <v-icon size="24px">
              {{ icon }}
            </v-icon>
          </v-btn>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-text class="white--text">
          {{ new Date().getFullYear() }} — <strong>Blog Exemplo</strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
import apresentation from '../components/apresentation.vue'
export default {
  components: { apresentation },
  name: 'DefaultLayout',
  data () {
    return {
      fixed: false,
      title: 'Blog Exemplo',
      icons: [
        'mdi-whatsapp',
        'mdi-linkedin',
        'mdi-facebook',
        'mdi-instagram',
      ],
      items: [
        'default',
        'absolute',
        'fixed',
      ],
      padless: false,
      variant: 'default',
    }
  }
}
</script>

<style scoped>

a.nuxt-link {
  text-decoration: none;
  font-weight: bolder;
}

</style>>

