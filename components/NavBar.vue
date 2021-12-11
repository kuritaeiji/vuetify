<template>
  <nav>
    <v-app-bar flat color="grey lighten-4">
      <v-app-bar-nav-icon @click="drawer = !drawer" />
      <v-app-bar-title class="grey--text text-uppercase">
        <span class="font-weight-light">Todo</span>
        <span>ninja</span>
      </v-app-bar-title>

      <v-spacer />

      <v-menu offset-y>
        <template #activator="{ on, attrs }">
          <v-btn text color="grey" v-bind="attrs" v-on="on">
            <v-icon left>
              mdi-chevron-down
            </v-icon>
            <span>Menu</span>
          </v-btn>
        </template>
        <v-list>
          <v-list-item v-for="link of links" :key="link.text" :to="link.route">
            <v-list-item-title>{{ link.text }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
      <v-btn text color="grey d-none d-md-flex">
        <span>Sign Out</span>
        <v-icon>mdi-exit-to-app</v-icon>
      </v-btn>
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      fixed
      hide-overlay
      class="purple lighten-2"
    >
      <v-row no-gutters class="text-center">
        <v-col>
          <v-avatar size="100" class="mt-4">
            <v-img :src="img" />
          </v-avatar>
          <p class="white--text text-subtitle-1 mt-2">
            The Net Ninja
          </p>
        </v-col>
        <v-col class="mb-4">
          <pop-up @addedProduct="openSnackbar" />
        </v-col>
      </v-row>

      <v-list>
        <v-list-item v-for="link of links" :key="link.text" :to="link.route">
          <v-list-item-action>
            <v-icon :class="linkColor">
              mdi-{{ link.icon }}
            </v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title :class="linkColor">
              {{ link.text }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-snackbar v-model="snackbar">
      {{ productTitle }}を追加しました
      <template #action="{ attrs }">
        <v-btn text color="white" v-bind="attrs" @click="snackbar = false">
          閉じる
        </v-btn>
      </template>
    </v-snackbar>
  </nav>
</template>

<script>
import img from '@/assets/avatar-1.png'

export default {
  data () {
    return {
      snackbar: true,
      productTitle: '',
      drawer: false,
      links: [
        { icon: 'view-dashboard', text: 'Dashboard', route: '/' },
        { icon: 'folder', text: 'My Projects', route: '/projects' },
        { icon: 'account', text: 'Team', route: '/team' }
      ],
      linkColor: 'white--text',
      img
    }
  },
  methods: {
    openSnackbar (title) {
      this.productTitle = title
      this.snackbar = true
    }
  }
}
</script>
