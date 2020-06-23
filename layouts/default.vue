<template>
  <v-app dark>
    <v-app-bar inverted-scroll fixed app>
      <v-app-bar-nav-icon @click="drawer = true" class="hidden-sm-and-up"></v-app-bar-nav-icon>
      <v-spacer></v-spacer>
      <v-spacer class="hidden-sm-and-up"></v-spacer>
      <v-img :src="images.logo" aspect-ratio="631.277" min-height="100%" contain></v-img>
      <v-spacer></v-spacer>
      <v-spacer></v-spacer>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn v-for="item in menu" :key="item.id" :to="item.link" text>{{ item.title }}</v-btn>
      </v-toolbar-items>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" absolute temporary width="300" style="position:fixed; top:0; left:0; overflow-y:scroll;">
      <v-list>
        <v-list-item v-for="item in menu" :key="item.id" :to="item.link">
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-content>
      <v-container style="padding:0px;">
        <nuxt />
      </v-container>
    </v-content>

    <v-footer dark padless>
      <v-card class="flex" flat tile>
        <v-card-title class="green">
          <strong class="subheading">Conéctate con nuestras redes sociales HOY!</strong>

          <v-spacer></v-spacer>

          <v-btn v-for="icon in icons" :key="icon.tittle" class="mx-4" dark icon>
            <v-icon size="24px">{{ icon.tittle }}</v-icon>
          </v-btn>
        </v-card-title>

        <v-card-text class="py-2 white--text text-center">
          <strong>Todos los derechos protegidos</strong>
          — {{ new Date().getFullYear() }} —
          <strong>Universidad de Medellín</strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      fixed: true,
      drawer: false,
      menu: [
        { id: 1, icon: 'mdi-home', title: 'INICIO', link: '/' },
        { id: 2, icon: 'mdi-tools', title: 'APLICACIONES', link: '/admin' },
        { id: 3, icon: 'mdi-phone', title: 'CONTACTO', link: '/about' },
        { id: 4, icon: 'mdi-face', title: 'INICIAR SESION', link: '/login' },
      ],
      images: {
        logo: require('../assets/img/comercial_name.png')
      },
      icons: [
        {
          tittle: 'mdi-facebook',
          target: 'https://www.facebook.com/'
        },
        {
          tittle: 'mdi-instagram',
          target: 'https://www.instagram.com/'
        }
      ]
    }
  },

  methods: {
    menuItems() {
      return this.menu
    }
  }
}
</script>