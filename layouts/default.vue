<template>
  <v-app dark>
    <v-navigation-drawer
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

    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title v-text="title" />
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    

    <v-footer
      app
    >
      <span>&copy; {{ new Date().getFullYear() }} 夜橘</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: '首頁',
          to: '/'
        },
        {
          icon: 'mdi-post-outline',
          title: '部落格',
          to: '/blog'
        },
        {
          icon: 'mdi-chart-bubble',
          title: '關於我們',
          to: '/introUs'
        },
        {
          icon: 'mdi-arrow-down-bold-box-outline',
          title: '下載',
          to: '/download'
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: '夜橘'
    }
  },

}
</script>
