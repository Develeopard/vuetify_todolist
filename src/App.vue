<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
    >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            Vuetify Todo List
          </v-list-item-title>
          <v-list-item-subtitle>
            My First Vuetify Project
          </v-list-item-subtitle>
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
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      color="primary"
      dark
      src="https://picsum.photos/1920/1080?random"
      prominent
      height="170"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>

      <v-container class="pa-0">
        <v-row>
          <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
          <v-spacer></v-spacer>
          <Search />
        </v-row>
        
        <v-row>
          <v-app-bar-title class="text-h4 ml-4">Vuetify Todo List</v-app-bar-title>
        </v-row>
        <v-row>
          <LiveTimeDate />
        </v-row>
      </v-container>

    </v-app-bar>

    <v-main>
      <router-view></router-view>
      <Snackbar />
    </v-main>
  </v-app>
</template>

<script>
import Search from '@/components/Tools/Search'
import LiveTimeDate from '@/components/Tools/LiveTimeDate'
import Snackbar from '@/components/Global/Snackbar'

  export default {
    data: () => ({ 
      drawer: null,
      items: [
        { title: 'Todo', icon: 'mdi-format-list-checks', to: '/'},
        { title: 'About', icon: 'mdi-help-box', to: '/about'},
      ], 
    }),
    components: {
      Search,
      LiveTimeDate,
      Snackbar,
    },
  }
</script>
