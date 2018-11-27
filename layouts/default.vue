<template>
  <v-app>
    <v-navigation-drawer
      :mini-variant="miniVariant"
      :clipped="clipped"
      v-model="drawer"
      fixed
      app
    >
      <v-list>
        <v-list-tile
          v-for="(item, i) in items"
          :to="item.to"
          :key="i"
          router
          exact
        >
          <v-list-tile-action>
            <v-icon v-html="item.icon" />
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title" />
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-toolbar-side-icon @click="drawer = !drawer" />

      <v-toolbar-title v-text="title"/>
        
    </v-toolbar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-navigation-drawer
      :right="right"
      v-model="rightDrawer"
      temporary
      fixed
    >
      <v-list>
        <v-list-tile @click.native="right = !right">
          <v-list-tile-action>
            <v-icon light>compare_arrows</v-icon>
          </v-list-tile-action>
          <v-list-tile-title>Switch drawer (click me)</v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>

    
    <v-footer
      :fixed="fixed"
      app
      class="pa-3"
    >  
      <v-spacer/>
      <div>&copy; {{ new Date().getFullYear() }}</div>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    data() {
      return {
        clipped: false,
        drawer: true,
        fixed: false,
        items: [
          { icon: 'apps', title: 'Массаж в майкопе', to: '/' },
          { icon: 'bubble_chart', title: 'Лечебный', to: '/lechebnyj-massazh' },
          { icon: 'bubble_chart', title: 'Спортивный', to: '/sportivnyj' },
          { icon: 'bubble_chart', title: 'Антицеллюлитный', to: '/anticelljulitnyj' },
          { icon: 'bubble_chart', title: 'Медовый', to: '/medovyj' },
          { icon: 'bubble_chart', title: 'Детский', to: '/detski' },
          { icon: 'apps', title: 'Сертификат, Мед.Диплом', to: '/sertifikat' }
        ],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'Массаж в майкопе!'
      }
    }
  }
</script>
