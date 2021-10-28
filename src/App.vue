<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      :mobile-breakpoint="768"
      app
    >
      <v-img
        height="170"
        src="https://picsum.photos/1920/1080?random"
        gradient="to top right, rgba(19,84,122,.2), rgba(128,208,199,.5)"
        class="pa-4 pt-7"
      >
      <v-avatar size="70" class="mb-2">
        <img
          src="https://cdn.vuetifyjs.com/images/john.jpg"
          alt="John"
        >
      </v-avatar>
      <div class="white--text text-subtitle-1 font-weight-bold">John Doe</div>
      <div class="white--text text-subtitle-2">john__doe</div>
      </v-img>

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
      :height="$route.path === '/' ? '238' : '170'"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.8), rgba(128,208,199,.9)"
        ></v-img>
      </template>

      <v-container class="header-container pa-0">
        <v-row>
          <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
          <v-spacer></v-spacer>
          <Search />
        </v-row>
        
        <v-row>
          <v-app-bar-title class="text-h4 ml-4">{{ $store.state.appTitle}}</v-app-bar-title>
        </v-row>
        <v-row>
          <LiveTimeDate />
        </v-row>
        <v-row v-if="$route.path === '/'">
          <FieldAddTask />
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
import FieldAddTask from '@/components/Todo/FieldAddTask';
import Snackbar from '@/components/Global/Snackbar'

  export default {
    data: () => ({ 
      drawer: null,
      items: [
        { title: 'Todo', icon: 'mdi-format-list-checks', to: '/'},
        { title: 'About', icon: 'mdi-help-box', to: '/about'},
      ], 
    }),
    mounted() {
      this.$store.dispatch('getTasks')
    },
    components: {
      Search,
      LiveTimeDate,
      FieldAddTask,
      Snackbar,
    },
  }
</script>

<style lang="scss">
  .header-container{
    max-width: none !important;
  }
</style>