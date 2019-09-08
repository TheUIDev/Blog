<template>
  <v-app dark>
    <v-navigation-drawer
      dark
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title v-text="title" />
    </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer dark padless>
      <v-card class="flex" flat tile>
        <v-card-title class="light-blue">
          <div class="flex-grow-1"></div>
          <v-btn v-for="icon in icons" :key="icon" class="mx-4" dark icon>
            <a :href="icon.link" class="social-links" target="_blank">
              <v-icon size="24px">{{ icon.class }}</v-icon>
            </a>
          </v-btn>
        </v-card-title>

        <v-card-actions class="grey darken-3 justify-center">
          &copy; {{ new Date().getFullYear() }} —&nbsp;
          <strong>Shreerang Patwardhan</strong>
        </v-card-actions>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      icons: [
        {
          class: 'mdi-twitter',
          link: 'https://twitter.com/shreerangp/'
        },
        {
          class: 'mdi-linkedin',
          link: 'https://www.linkedin.com/in/shreerangp/'
        }
      ],
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Blog',
          to: '/blog'
        },
        {
          icon: 'mdi-language-javascript',
          title: 'ES6 Series',
          to: '/es6-101-series'
        },
        {
          icon: 'mdi-google-maps',
          title: 'Google Maps Series',
          to: '/google-maps-series'
        },
        {
          icon: 'mdi-cellphone-link',
          title: 'jQuery Mobile Series',
          to: '/jquery-mobile-series'
        }
      ],
      miniVariant: false,
      title: 'The UI Dev'
    }
  }
}
</script>
<style lang="scss" scoped>
.v-application a {
  color: #fff;
}
</style>
