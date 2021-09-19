<template>
  <v-app>

    <v-navigation-drawer
      temporary
      app
      v-model="drawer"
    >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            Menu
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>
      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.link"
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer
>

    <v-app-bar
      dense
      dark
      app
    >
      <v-app-bar-nav-icon
        @click.stop="drawer = !drawer"
        class="hidden-md-and-up"
      >
      </v-app-bar-nav-icon>

      <v-toolbar-title @click="$router.push('/')">Test App</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn
        plain
        elevation="2"
        v-for="item in items"
        :key="item.title"
        :to="item.link"
        class="hidden-sm-and-down"
      >{{ item.title }}
        <v-icon right>
          {{ item.icon }}
        </v-icon>
      </v-btn>

    </v-app-bar>
    <v-content>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      drawer: false,
      items: [
        {title: 'sign in', 'icon': 'mdi-login-variant', link: '/login'},
        {title: 'sign up', 'icon': 'mdi-account-plus-outline', link: '/register'},
        {title: 'Dashboard', icon: 'mdi-view-dashboard', link: '/dashboard'}
      ],
      right: null
    }
  }
}
</script>

<style>

</style>
